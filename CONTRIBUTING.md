# How to contribute

First of all, thank you for wanting to contribute! We really appreciate all the awesome support we get from our community. We want to keep it as easy as possible to contribute changes that get things working in your environment. There are a few guidelines we need contributors to follow to keep the project flowing smoothly.

## Branches

There is a single mainline branches `master` which is used for trunk-based development work. All new features, changes, etc. must be applied to `master`.

## Making changes

1. [Fork](http://help.github.com/forking/) on GitHub
1. Clone your fork locally
1. Configure the `upstream` repo (`git remote add upstream git://github.com/OpenVASP/openvasp-specification.git`)
1. Checkout `master` (`git checkout master`)
1. Create a local branch (`git checkout -b my-branch`). The branch name should be descriptive, or it can just be the GitHub issue number which the work relates to, e.g. `123`.
1. Work on your change
1. Rebase if required (see 'Handling updates from `upstream`' below)
1. Test the build locally
1. Push the branch up to GitHub (`git push origin my-branch`)
1. Send a pull request on GitHub (see 'Sending a Pull Request' below)

You should **never** work on a clone of `master`, and you should **never** send a pull request from `master`. Always use a feature/patch branch. The reasons for this are detailed below.

## Handling updates from `upstream`

While you're working away in your branch it's quite possible that your `upstream` `master` may be updated. If this happens you should:

1. [Stash](https://git-scm.com/book/en/v2/Git-Tools-Stashing-and-Cleaning) any un-committed changes you need to
1. `git checkout master`
1. `git pull upstream master --ff-only`
1. `git checkout my-branch`
1. `git rebase master my-branch`
1. `git push origin master` (optional) this keeps `master` in your fork up to date

These steps ensure your history is "clean" i.e. you have one branch from `master` followed by your changes in a straight line. Failing to do this ends up with several "messy" merges in your history, which we don't want. This is the reason why you should always work in a branch and you should never be working in or sending pull requests from `master`.

If you're working on a long running feature you may want to do this quite often to reduce the risk of tricky merges later on.

## Sending a pull request

While working on your feature you may well create several branches, which is fine, but before you send a pull request you should ensure that you have rebased back to a single "feature/patch branch". We care about your commits, and we care about your feature/patch branch, but we don't care about how many or which branches you created while you were working on it. :smile:

When you're ready to go you should confirm that you are up to date and rebased with `upstream` `master` (see "Handling updates from `upstream`" above) and then:

1. `git push origin my-branch`
1. Send a descriptive [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) on GitHub.
   - Make sure the pull request is **from** the branch on your fork **to** the `OpenVASP/openvasp-csharp-client` `master`.
   - If your changes relate to a GitHub issue, add the issue number to the pull request description in the format `#123`.
1. If GitHub determines that the pull request can be merged automatically, a test build will commence shortly after you raise the pull request. The build status will be reported on the pull request.
   - If the build fails, there may be a problem with your changes which you will have to fix before the pull request can be merged. Follow the link to the build server and inspect the build logs to see what caused the failure.
   - Occasionally, build failures may be due to problems on the build server rather than problems in your changes. If you determine this to be the case, please add a comment on the pull request and one of the maintainers will address the problem.

## What happens next?

The maintainers will review your pull request and provide any feedback required.
