Title: Git Ready
Date: 2015-07-15 12:13
Modified: 2015-07-15 12:13
Category: Brain-Dump
Authors: Chris Osltrom, Nikki Martinez
Summary: How to use git-ready

# git-ready

git-ready is a tool for quickly joining an organization on GitHub.

Description
-----------

git-ready does three things.
1. Forks all repositories of the organization to your account.
2. Clones the forked repositories locally.
3. Configures an `upstream` remote for each repository, for convenient fetching.

It can be run again without concern. It will only fork and clone missing repositories.

Installation
------------

`gem install git-ready`

`git-ready telusdigital`

Configuration
-------------
git-ready will search for configuration files in the following places:
* /etc/git-ready.yaml
* /usr/local/etc/git-ready.yaml
* ~/.config/git-ready.yaml
* ./git-ready.yaml

These will be loaded in order, and any conflicting keys will be overwritten.

If your GitHub account uses 2-Factor Authentication, git-ready will prompt you for a 2FA token. If you don't have 2-Factor Authentication, get it....please.

OSX Installation Issues?
------------------------

One of the gems used by git-ready ([Rugged](https://github.com/libgit2/rugged)), requires `cmake` and `libgit2` to build. On OSX, this isn't installed by default, but can easily be resolved with `brew install cmake`, `brew install libgit2 --with-libssh2` .

Also, private key has to be registered in keychain in order to repo cloning works.

If you are still having problems, check the version of your OpenSSH. (`ssh -V`) Keychain support is in version 6.8
