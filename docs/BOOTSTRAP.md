# Bootstrap and push

## Package contents

This is a compact workspace shell: charter, registry, manifests, session templates and empty research/package locations. It intentionally contains no existing application repository history or source files.

## Create the remote and import

Run these steps from the prepared package on the authorized VPS connection. The expected destination is a new **public** repository `rock-solid-sites/atproto-workspace`; create it empty, without GitHub's auto-generated README, so the local initial commit can be pushed without unrelated history.

```sh
set -eu
cd /path/to/atproto-workspace-bootstrap
python3 -m json.tool workspace.manifest.json >/dev/null
python3 -m json.tool projects/registry.json >/dev/null
test -f CHARTER.md && test -f README.md
git init -b main
git add README.md CHARTER.md workspace.manifest.json projects docs templates research packages
git commit -m "chore: bootstrap ATProto workspace"
gh repo create rock-solid-sites/atproto-workspace --public --description "Shared governance and development workspace for independent ATProto projects" --source . --remote origin --push
```

If `gh repo create` reports that the repository already exists, stop and inspect its owner, visibility, branches and contents. Do not overwrite, force-push, or change an existing repository's upstream. Import only after confirming that the exact destination is empty and intended for this package.

## Verify the pushed state

```sh
git status --short
git remote -v
git rev-parse HEAD
gh repo view rock-solid-sites/atproto-workspace --json name,url,isPrivate,defaultBranchRef
```

Confirm a clean worktree, `main` as the default branch, public visibility, and the expected commit on GitHub. Record the commit SHA and repository URL in the handoff/closure note. Do not add existing project remotes to this umbrella repository.

## First follow-up

Resolve the ATProto Thread Reader's canonical source location and update `projects/registry.json` with its real upstream/ref. Obtain the current `100percentaiart` commit. Review source licensing and publication boundaries before considering submodules or snapshots. Keep Atmosphere Free Stack as reference-only and retain its private upstream.
