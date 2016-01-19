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
- All branch names should be prefixed with "feature/", "bug/", "chore/", "hot-fix/", or "spike/",
  followed by a concise description.
- `rebase` regularly up until you publish your branch. Do *NOT* `rebase` after publishing your
  branch, as this will rewrite public history and can cause pain for the rest of the team.

## Commits
Follow these [guidelines](http://chris.beams.io/posts/git-commit/#seven-rules):

- Separate subject from body with a blank line (when more than just subject is necessary)
- Limit the subject line to 50 characters
- Capitalize the subject line
- Do not end the subject line with a period
- Use the imperative mood in the subject line
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how

## Pull Requests
- The PR submitter is responsible for handling any reviewer requested changes. This only changes
  in the following scenarios:
  - The submitter requests assistance from a coworker and passes responsibility.
  - A coworker is free and desires to handle the changes, in which case they should notify the
    submitter via Slack or PR comments.
- Do *NOT* make changes to a PR for which you do not possess responsibility.
