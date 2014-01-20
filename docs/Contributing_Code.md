## Introduction
Since Ringmaster is a fully open-source app, we would appreciate if you dive in and start adding features, fixing bugs, and cleaning up the code.

## How to contribute

Third-party patches are essential for keeping Ringmaster great. We simply can't access the huge number of platforms and  myriad configurations for running Ringmaster. We want to keep it as easy as possible to contribute changes that get things working in your environment. There are a few guidelines that we need contributors to follow so that we can have a chance of keeping on top of things. 

* Make sure you have a [GitHub Account](https://github.com/signup/free)
* Submit a ticket for your issue, assuming one does not already exist.
  * Clearly describe the issue including steps to reproduce when it is a bug.
  * Make sure you fill in the earliest version that you know has the issue.
* Fork the repository on GitHub

## Making Changes
* Get the latest code from Github
  * Fork the Main Ringmaster repository.
  * Clone your fork of the Ringmaster repository.
* Add a remote for the main Ringmaster repo 
  * To make things easier to integrate and to keep your fork up to date then you need to add the main Ringmaster repo as a remote reference.
  * `git remote add upstream https://github.com/DamageStudios/ringmaster.git`
  * Then, when you need to pull the latest from the main Ringmaster repo, you just fetch and merge the MASTER branch:
  * `git fetch upstream`
  * `git merge upstream/master`
  * You can also use `git pull upstream master` if you want it all in one step.
* Make a branch for your changes
  * Create a branch from where you want to base your work.
  * Generally you'll want to branch from __MASTER__
  * Please use the naming convention "ringmaster-[issue-num]" for your branch name to help us keep track of what your patch actually fixes
* Push your code and make a pull request
 * One pull request per issue. Do NOT try and fix multiple issues with a single pull request.
 * Please make your commit messages and pull requests informative. i.e. `moved version string to git_revision Fixes #123`. By using the Fixes/Fixed #Issue-Number in the commit message it will allow for closing of issues once the pull request is merged. For more information please read [this](https://github.com/blog/831-issues-2-0-the-next-generation).
 * Push your changes to your fork of the repository. 
 * `git push origin ringmaster-[issue-num]`
 * Submit a pull request to the Ringmaster main repository.

At this point you're waiting on us. We like to at least comment on, if not accept, pull requests within three business days (and, typically, one business day). We may suggest some changes or improvements or alternatives.

## Additional Resources
* [Issue tracker](https://github.com/DamageStudios/ringmaster/issues)
* [General GitHub documentation](http://help.github.com/)
* [GitHub pull request documentation](http://help.github.com/send-pull-requests/)