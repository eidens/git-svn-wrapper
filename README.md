sing - a git-svn wrapper
========

Provides wrappers for the git-svn workflow I've been using.
Uses a local master branch to fetch from/dcommit to its upstream svn branch; avoids any non-fast-forward merges into master to preserve linear history (see the caveats section of git help svn).


Usage
--------
    sing start feature/1
create and checkout branch feature/1 based on master, or checkout branch feature/1 if it already exits.
    // do work
    git commit -m -a "did work"
    
    sing update
fetch updates from svn, then rebase master on the svn head revision and the current branch on master

    // do some more work
    git commit ...

    sing finish feature/1
* updates feature/1 (see sing update)
* merge feature/1 into master: guaranteed to be fast-forward, thereby preserving linear history
* dcommit from master: with flag --interactive by default
* if successful, archive feature/1 as the tag archive/feature/1, then delete it