# GitHub Actions + GitVersion release demo

Demo repo for the post [Automatic Version Tag and Release with GitHub Actions and GitVersion](https://gdservices.io/automatic-version-tagging-and-release-with-github-actions/).

Every merge to `main` runs `tag-release-version`: GitVersion 6 works out the next semantic version from the branch that was merged, and the workflow creates the tag and a GitHub release with generated notes.

- `GitVersion.yml` uses the `TrunkBased/preview1` workflow preset (GitVersion 6 removed the old `Mainline` mode).
- Merging a `feature/*` branch bumps the minor version; merging a `hotfix/*` branch bumps the patch.
- The workflow needs `contents: write`. If your repo or org defaults `GITHUB_TOKEN` to read-only, the `permissions` block in the workflow takes care of it.
- Use merge commits (not squash) so GitVersion can see the source branch name.

To try it, fork the repo, create a `feature/...` branch, add a file, open a PR and merge it.
