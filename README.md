This repo is a git mirror of the svn repo:
https://svn.java.net/svn/uel~svn/trunk

All branches underneath svn/ are an exact copy and should not be modified (unless you have commit rights and plan on using dcommit)

All normal git "fork" branches are at the root repo.

They are:

2.0.4-b09-jbossorg - jboss patches against svn/tags/2.0.4-b09
2.1.3-b02-jbossorg - jboss patches against svn/tags/2.1.3-b02
mojarra-1.2        - Copy of the last 1.2 release source jar
master             - Instructions

These can be pushed just like any normal git branch.

= SVN MIRRORING

To be able to sync the source mojarra subversion commits to this repo, run git config -e and add:

[svn-remote "svn"]
        url = https://svn.java.net/svn/uel~svn
        fetch = :refs/remotes/git-svn
        branches = branches/*:refs/remotes/svn/*
        tags = tags/*:refs/remotes/svn/tags/*
[remote "svn-mirror"]
        url = https://github.com/jboss/uel.git
        push = refs/remotes/svn/*:refs/heads/svn/*

Then type:
git svn fetch

This takes a very very long time to build the metadata.

Once this is complete you can now run the following to sync the latest:

git svn fetch
git push svn-mirror
