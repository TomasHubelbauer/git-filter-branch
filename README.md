# Git `filter-branch`

This repository has a GitHub Actions workflow associated with it. The workflow
runs on each push and on an hourly schedule and in each run, it removes `docs`
including its history (by rewriting entire repository history) and then runs a
script which generates new `docs` with fresh content. As a result, the content
of `docs` (which is auto-generated) doesn't make the repository grow in size
uncontrollably.

## To-Do

### Verify the script works as intended
