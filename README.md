A simple set of scripts for working with GitHub on the command line.

Setup
=====
1. Clone this repo

    `git clone git@github.com:rbrainard/github.git`

2. Create a symlink to the script in `bin/github` :

    `ln -s <base_dir>/github/bin/github /usr/local/bin/github`

3. The first time you run this script, you will be prompted for additional configuration.


Commands
========

clone
-----

The `clone` command wraps `git clone`, but instead of naming the GitHub remote repo `origin`,
it uses the convention `github/<github_username>`, which is more fork-friendly. That is, 
this naming convention makes it easier to manage working with multiple forks of the same
repo on GitHub and/or with other Git servers. Additionally, if you are cloning another user's
repo, the script will automatically add a remote with the name `github/<your_github_username>`.
This does not actually setup the fork on GitHub, but saves you thr trouble of the local configuration
if you already have a fork or plan to create one in the future. 

The origin prefix defaults to `github/`, but can be customized if you want something different, such as `origin-`.
You are prompted for the prefix on first run, but can be changed later by setting the git config `github.originPrefix`.

Usage:
    
    github clone <git_url>

For example:

    github clone git@github.com:someone_else/interesting_project.git

would clone the repo to the dir `interesting_project` just like normal `git clone` would do,
but the remotes would be:

    github/someone_else git@github.com:someone_else/interesting_project.git
    github/you          git@github.com:you/interesting_project.git
