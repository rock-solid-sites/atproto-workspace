# ATProto Workspace

An umbrella workspace for research and development of independent ATProto tools. It holds shared governance, project records, cross-project research and reusable packages while each project keeps its own repository, release path and upstream ownership.

## Start here

1. Read the [Public-Interest Design Charter](CHARTER.md).
2. Review the [project registry](projects/registry.json) and [source map](projects/README.md).
3. Read the [workspace manifest](workspace.manifest.json) and [bootstrap instructions](docs/BOOTSTRAP.md).
4. For a new coding session, copy [the handoff template](templates/session-handoff.md) and fill only decision-relevant context.

## Contents

- `CHARTER.md` — shared evaluation commitments and review prompts.
- `workspace.manifest.json` — workspace identity, policy and source boundaries.
- `projects/registry.json` — project identity, canonical source, lifecycle and integration mode.
- `projects/README.md` — how project sources are added without taking ownership away from upstreams.
- `docs/` — bootstrap and ASES-informed session handoff practice.
- `templates/` — project manifest and session handoff templates.
- `packages/` — reserved for components intentionally built here or explicitly vendored.
- `research/` — cross-project evidence and design decisions, each with provenance.

No application source has been imported. The registry is the boundary between the umbrella workspace and independently owned repositories.

## Bootstrap status

This package is a source-ready starter. It does not claim a built or deployed ATProto stack, production PDS, verified recovery, or final product scope. See the manifest for verified upstream references and unresolved source identity.
