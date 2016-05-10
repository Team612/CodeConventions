#Github Style Guide
These rules are meant as guidelines for commit messages and branching for FIRST
Team 612. These are not hard-and-fast rules; all actions in git should first and
foremost be made for logical reasons. However, these guidelines allow consistency
and repository readability to be maintained throughout build season. Do not break
them without a good reason to.

## Branches

### Naming
The following are conventions for naming and using branches. Overall, If your branch
does not follow these conventions it may be removed without warning.

#### Prefixes
With few exceptions, valid branch names have one of the following prefixes:

* *dev* - a branch that contains a new feature to the code. Example: `dev-pneumatics`

* *fix* - a branch that fixes any problem with existing code, whether it be debugging
or formatting Example: `fix-segfault`

* *ut* - a unit testing branch. `ut-new_shooter`

* *kitbot* - any branches off the kitbot branch. These types of branches should be
kept to a minimum on the repository and removed as soon as possible. Consider
creating a ut branch before branching off the kitbot branch.
Example: `kitbot-swerve_drive`

#### Special naming cases
The following are special branches repository that do not need prefixes:  

* *master* - the most up to date version of the code. master must compile at all
times. Do not merge into master without permission from the programming captain.

* *workingcode* - the latest code used during a competition. This branch must
compile and run properly at all times.

* *kitbot* - the code for the kitbot.

* *gh-pages* - a detailed copy of the WPI libraries made in Doxygen.

#### Formatting
Branch names should be in lower\_case. The names should be a *short* description of
the branch. As a general rule the branch name is too long if it requires more than one
underscore. The code in the branch should be directly related to the branch name.

### Orphan Branches
Orphan branches are to be used for unit testing and for code for the kitbot branch.
Once the code for the unit test has been tested and confirmed working, the branch is
to be deleted and new code must be written based on what was what was learned during
unit testing. **Do not write code for the main repository in an orphan branch**.
If you are not sure whether or not you should be using an orphan branch, **don't
make one**.

## Commits
While commit messages do not always have to be 100% serious and/or professional,
they should be civil. The types commit messages should follow these guide.

### Swearing
Swearing should be used extremely sparingly. It is understandable to get frustrated
over something and take it out on a commit message. However the goal is to not fill
the repository with curse words. Remember that the repository is public and reflects
our team in general.

Swearing cases will be handled on an individual basis, ***but it is preferred members
not swear at all***. This would be a example of swearing in a commit message that
*may* be considered acceptable (provided the user didn't commit like this on a
regular basis):

    Changed the Execute() method in the Drive command to be less crappy.

This example would not be acceptable under any circumstance.

    Finally fucking fixed the shitty command that some other asswipe fucking wrote.

### Content
Commit messages should be descriptive of what's in the commit. A commit message
such as `changes` or `fixed stuff` is unacceptable.

Commit messages that insult others or blame other members for a problem will not
be accepted in PRs. For example:

    Fixed Ahmad's screw-up in OI.h

is not acceptable. However

    Fixed spelling mistake in OI.h

would be.
