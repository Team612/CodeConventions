#Github Style Guide
These rules are meant as guidelines for commit messages and branching for FIRST
Team 612. These are not hard-and-fast rules; all actions in git should first and
foremost be made for logical reasons. However, these guidelines allow consistency
and repository readability to be maintained throughout build season. Do not break
them without a good reason to.

## Branches

### Naming
The following are conventions for naming and using branches. If your branch does
not follow these conventions it will be removed without warning.

#### Prefixes
With few exceptions, valid branch names have one of the following prefixes:

* *dev* - a branch that contains a new feature to the code.

* *fix* - a branch that fixes any problem with existing code, whether it be debugging
or formatting

* *ut* - a unit testing branch.

#### Static branches
The following branches are a given in the repository  

* *master* - the most up to date version of the code.

* *working code* - the latest code used during a competition.

* *kitbot* - the code for the kitbot.

* *gh-pages* - a detailed copy of the WPI libraries made in Doxygen.

#### Naming
Branch names should be in lower\_case. The names should be a *short* description of
the branch. The code in the branch should be directly related to the branch name.

### Orphan Branches
Orphan branches are to be used for unit testing and for code for the kitbot. Once
the code for the unit test has been tested and confirmed working, the branch is to
be deleted. **Do not write code for the main repository in an orphan branch**. If
you are not sure whether or not you should be using an orphan branch, **don't**.

## Commits
While commit messages do not always have to be 100% serious and/or professional,
they should be civil. The types commit messages Follow these guide
