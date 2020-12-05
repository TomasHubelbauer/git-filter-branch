# Git `filter-branch`

This repository has a GitHub Actions workflow associated with it. The workflow
runs on each push and on an hourly schedule and in each run, it removes `docs`
including its history (by rewriting entire repository history) and then runs a
script which generates new `docs` with fresh content. As a result, the content
of `docs` (which is auto-generated) doesn't make the repository grow in size
uncontrollably.

## Downsides

Having a process rewrite the repository history on the remote this way is all
good and well it terms of having an automation clean up your repository so you
don't have to, but the force pushes from the workflow to the repository make
it super awkward to pull changes locally. You have to reset each time basically:

```
git pull --rebase
```

Also, there is a short window of time in which your push to the remote will
fail because it has just undergone the force push and you haven't checked out
the new history so you have to fiddle around with transplating your change
onto the new history.
