# Git

## Flow
- Create a topic branch off of `origin/master`.
- `rebase` against `origin/master` frequently.
- Squash your commits into logical groups (more on that [here](https://davidwalsh.name/squash-commits-git)).
- Push your topic branch to `origin`.
- Submit a pull request to `master` or `staging`. Apply the appropriate label(s).
- Receive approval from at least one reviewer.
- Merge your branch via GitHub and delete your topic branch.
- Immediately deploy the appropriate environment.

## Branches
- All branch names should be prefixed with one of the following: "feature", "bug", or "hot-fix".
- `rebase` regularly up until you publish your branch. Do *NOT* `rebase` after publishing your branch, as this will rewrite public history and can cause pain for the rest of the team.

## Commits
- Capitalize your commit messages.
- Start your message with a verb.
- Use present tense.
