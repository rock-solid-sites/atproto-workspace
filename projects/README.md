# Project registry and source boundaries

`registry.json` is an index, not a source mirror. Each project keeps its canonical upstream, issue history, releases and ownership unless a separate decision authorizes a change.

## Adding or integrating a project

1. Confirm the exact repository URL, owner, visibility, default branch and current commit from an authoritative source.
2. Record its license, any submodules or large-file requirements, and whether its contents may be published here.
3. Choose the smallest integration mode:
   - **Reference-only** (default): track purpose, status, source and decisions without importing code.
   - **Submodule**: link to the upstream repository while preserving its independent history and release process.
   - **Vendored snapshot**: copy a reviewed component with source commit, license notices, local modifications and update procedure documented.
   - **Native package**: create new code here when it is intentionally owned and released from this workspace.
4. Record the reason and review date in the registry. Never rewrite an upstream remote or history as part of routine onboarding.
5. If source identity, license, privacy classification or ownership is unclear, leave the project reference-only and record the unresolved fact.

Do not place secrets, user exports, private keys, provider credentials or production data in this public workspace.
