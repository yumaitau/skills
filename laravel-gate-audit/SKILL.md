---
name: laravel-gate-audit
description: Use this skill when auditing a Laravel application for authorization gate and policy usage, especially requests like "find missing gates", "audit Gate::allows", "check @can permissions", "verify policies", or "find undefined abilities". It traces ability usage across controllers, models, Blade, Livewire, routes, jobs, tests, and middleware, then compares each usage against Gate::define declarations, policy methods, policy mappings, and before/after hooks to report missing or suspicious definitions.
---

# Laravel Gate Audit

Audit Laravel authorization usage by comparing every referenced ability with the places Laravel can define or resolve that ability. The goal is to find missing definitions, typo-level mismatches, stale checks, and checks that rely on implicit policies without enough evidence.

Write the audit report in Australian English. Defer spelling detail to the `australian-english` skill; leave code identifiers, ability strings, class names, and file paths spelled exactly as they appear in the codebase.

## Audit Scope

Inspect gate and policy ability usage in:

- controllers, form requests, actions, services, jobs, listeners, middleware, commands, models, and tests
- Blade directives such as `@can`, `@cannot`, `@canany`, `@elsecan`, and `@elsecannot`
- code calls such as `Gate::allows`, `Gate::denies`, `Gate::check`, `Gate::authorize`, `Gate::inspect`, `Gate::any`, `Gate::none`, `can`, `cant`, `cannot`, `authorize`, `authorizeForUser`, and route middleware using `can:`
- Livewire, Inertia, Nova, Filament, API resource, or package-specific authorization wrappers when present

Inspect gate and policy definitions in:

- `Gate::define`, `Gate::resource`, `Gate::before`, and `Gate::after`
- `AuthServiceProvider`, custom service providers, route/service bootstrapping files, and package providers
- policy classes under `app/Policies` or project-specific policy directories
- policy mappings in `Gate::policy`, `$policies`, service providers, package config, and auto-discovered policy names
- policy methods including `viewAny`, `view`, `create`, `update`, `delete`, `restore`, `forceDelete`, and custom ability methods

## Working Method

1. Identify the Laravel version and project shape. Check `composer.json`, `app/Providers`, `bootstrap/app.php`, `routes/`, `app/Policies`, and test folders.
2. Build an ability usage inventory. Record the ability string, file, line, call style, subject/model argument when available, and any user override.
3. Build a definition inventory. Record explicit gates, resource gates, policy mappings, policy class methods, global hooks, and package-provided definitions.
4. Match each usage to a definition using Laravel's resolution rules, not just string equality.
5. Report definite missing definitions separately from uncertain or dynamic cases.
6. Include enough evidence for each finding: file path, line number, ability, subject/model, expected definition location, and why it appears missing.

## Search Commands

Use `Grep`/`Glob` first when available. When shell search is more efficient, run ripgrep from the repo root.

Find common ability usages:

```bash
rg -n "Gate::(allows|denies|authorize|inspect|any|none|check)|->(can|cant|cannot)\(|\b(can|cant|cannot)\(|\$this->authorize\(|authorizeForUser\(|@can\b|@cannot\b|@canany\b|@elsecan\b|@elsecannot\b|can:" . -g "*.php" -g "*.blade.php"
```

Find definitions and policy wiring:

```bash
rg -n "Gate::(define|resource|policy|before|after)|protected \$policies|class .*Policy|function (viewAny|view|create|update|delete|restore|forceDelete|before|after)\b" . -g "*.php"
```

If the repo has large generated or vendor folders, exclude them with `-g '!vendor/**'`, `-g '!storage/**'`, or project-specific generated paths.

## Matching Rules

- For `Gate::define('ability', ...)`, match the exact ability string.
- For `Gate::resource('posts', PostPolicy::class)`, expand the generated ability names before reporting anything missing.
- For `$user->can('update', $post)`, `$this->authorize('update', $post)`, and route middleware like `can:update,post`, match `update` against the policy resolved for the subject model.
- For `@can('update', $post)`, match like `$user->can('update', $post)`.
- For `@can('manage-users')` or `Gate::allows('manage-users')` without a model argument, expect an explicit gate unless the project has a documented convention that maps string abilities elsewhere.
- Treat policy `before` methods and `Gate::before` hooks as broad allow/deny hooks, not as proof that every named ability is intentionally defined.
- Treat dynamic ability names such as `$user->can($ability, $model)` as uncertain unless the variable can be resolved locally or from a constant/enum.
- Check enum or constant-backed abilities before declaring a string missing. Search for the enum case or constant value and its consumers.
- If Laravel auto-discovery is in use, a model `App\Models\Post` can resolve to `App\Policies\PostPolicy` without an explicit `$policies` entry. Verify class existence and method names.
- For `authorizeResource`, inspect the controller model and compare the generated controller abilities against the target policy methods.

## Report Format

Start with a short summary and counts:

- total ability usages found
- definite missing definitions
- suspicious mismatches
- dynamic or unresolved usages

Then list findings by severity: missing definitions first, then suspicious mismatches, then dynamic unresolved usages.

For each finding include:

- `file:line`
- ability name
- call style, for example `Gate::allows`, `@can`, `can:` middleware, or `$this->authorize`
- subject/model argument if present
- expected definition, for example `Gate::define('publish posts')` or `PostPolicy::publish`
- evidence checked, for example searched providers, policy mappings, and policy class methods
- suggested minimal fix

Use these categories:

- **Missing definition**: ability has no explicit gate and no resolvable policy method.
- **Suspicious mismatch**: likely typo, wrong subject model, pluralisation mismatch, or policy method name mismatch.
- **Dynamic unresolved**: ability is variable-driven and cannot be proven from static search.
- **Covered**: optional section for important abilities that are correctly defined.

### Example finding

> **Missing definition** — `app/Http/Controllers/PostController.php:48`
> - ability: `publish`
> - call style: `$this->authorize('publish', $post)`
> - subject: `App\Models\Post`
> - expected definition: `App\Policies\PostPolicy::publish`
> - evidence checked: `PostPolicy` exists and resolves for `Post` via auto-discovery but has no `publish` method; no `Gate::define('publish', ...)` in any registered provider; no `before` hook grants it for normal users
> - suggested fix: add `public function publish(User $user, Post $post): bool` to `PostPolicy`

## Common Laravel Edge Cases

### Laravel 11+ provider layout

Laravel 11 apps may not have the older `app/Providers/AuthServiceProvider.php`. Check `bootstrap/app.php`, `AppServiceProvider`, package providers, and any provider registered in `bootstrap/providers.php` before reporting missing gates.

### Policy auto-discovery

Laravel can discover policies by naming convention. Do not require `$policies` mappings when the policy class exists in the expected namespace and contains the needed method.

### Resource gates and controllers

`Gate::resource` and controller `authorizeResource` both expand into multiple abilities. Expand them before matching so generated abilities are not falsely reported as missing.

### Super-admin hooks

Global `Gate::before` or policy `before` methods can short-circuit authorization for privileged users. They do not replace ability definitions for normal users, so still report missing explicit gates or policy methods.

### Package permissions

Projects using packages such as Spatie Permission often check permissions through gates or `can` middleware. Verify whether package service providers register those permissions as gates before marking them missing.

## Verification

Before finalising the audit:

1. Re-run the usage and definition searches after expanding non-standard folders.
2. Spot-check at least one finding from each category by reading the surrounding code.
3. If tests exist for authorization, identify the relevant test command but do not claim a missing definition is fixed unless the user asked you to change code and tests pass.
4. Make clear which findings are static-analysis confidence and which need runtime confirmation.

## When NOT To Use

- Do not use this for a general Laravel security audit unless the task specifically includes gates, policies, abilities, permissions, or authorization checks.
- Do not use this for authentication issues such as login, guards, sessions, password reset, Sanctum tokens, or OAuth unless they interact with gate/policy checks.
- Do not use this for database role/permission modelling alone unless the request asks whether those permissions are wired into Laravel authorization.
