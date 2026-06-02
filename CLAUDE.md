# CLAUDE.md

This is an independently maintained fork of [ml-explore/mlx-swift](https://github.com/ml-explore/mlx-swift).

## Branches

- `main` mirrors upstream `main` and carries no local changes.
- `patches` is the working branch: upstream plus local patches, rebased onto each new upstream release. Downstream projects consume this branch — for example, swift-lm references it as `branch: "patches"`.

## Updating to a new upstream release

1. Fetch upstream: `git fetch upstream --tags`.
2. Rebase the patches onto the new release: `git rebase upstream/main patches`. Upstream `main` is normally at the latest release commit; rebase onto the release tag instead if you prefer to pin to a tag.
3. If upstream touched a patched file, resolve the conflicts, then confirm the patches replayed unchanged. Comparing the `git patch-id` of each patch commit before and after the rebase is a quick check.
4. Push the rewritten branch: `git push --force-with-lease origin patches`.
5. In each downstream project, repin the dependency: `swift package update mlx-swift`.

## Remotes

- `origin` → `https://github.com/DePasqualeOrg/mlx-swift.git` (this fork)
- `upstream` → `https://github.com/ml-explore/mlx-swift.git` (ml-explore)
