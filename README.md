#### Intro and notes
Some useful git scripts to make easier some daily operations.

Note that some of them are dependent of:

- The naming schema used for Moodle branches (MOODLE_XX[X]_STABLE)
- My very own naming schema used for feature branches (_21, _22, _310...)

But surely they can be easily hacked to suit your needs.

#### To install them

- Clone/download this repository.
- Add it to your `$PATH`.
- That's all, now you can run them from git.

#### Available scripts

##### `git cabra`
Returns all the authors (in `Co-authored by:` format) for the commits present in a branch since it was created from another, base one. Useful when going to squash lots of commits and, still, want to add that information in the final commit. 

##### `git currentbranch`
Returns the current branch.

##### `git currentcommit`
Returns the current commit (in specified branch, default to current).

##### `git mrproper`
Detects all the feature branches already merged/picked
upstream, suggesting the git command to execute in order to get rid of
them. Note that some ff merges can lead to undetected changes so it
only will be working 100% reliable if no ff merges are performed.

##### `git oldest-ancestor`
Returns the oldest common ancestor (branch point)
of two given branches.

##### `git overlapping`
Returns the overlapping factor between two related
commits. The overlapping factor is calculated as the product between
the % of commits having overlapping lines and the % of the lines
overlapping.    
Higher means, usually, worse (for a better looking history without
too many back and forth changes over the same lines (aka, overlapping).

##### `git package`
Given a commit/tag/branch, a format (zip, tar, tgz),
a target directory and a prefix generate one package containing
that exact version from any git repository. When a prefix is defined,
support for both including and excluding files is enabled if
prefix.includes or prefix.excludes files are present in the git dir.
Also, you can use one prefix.executes file to perform any other
customization before proceeding with packaging. See git-package-moodle-prefix
for a working example prefix). Examples:

- git package
- git package v2.2.3 --format=tgz --prefix=moodle
- git package MOODLE_22_STABLE --dir=/some/dir --prefix=moodle
- git package v2.1.0 -f tar -d /some/dir -p moodle
- git package 53cd3c286e8ac0b368fa6becb113945f292891cc
- git package v2.4.0-rc1 --branch MOODLE_24_STABLE
- git package v2.5-beta --ignoretags

##### `git pullall`
Pulls all the upstream branches.

##### `git resetall`
Resets all local branches to the status of upstream ones.

#### Copyrights, history and license

© various scripts, pages, examples out there I've used to build them.    
© 2012 and upwards, the code, Eloy Lafuente (stronk7).    
© 2012 and upwards, the "mrproper" name, David Mudrák.    

20121203 - Added git-currentcommit and git-package.    
20121220 - Added --branch and prefix.excludes support to git-package.    
20200820 - Added support to 3-digit branches.    
20201115 - Added new git overlapping utility.    
20240217 - Added new git cabra (co-authors in a branch) utility.    

License: Whatever you need, being OSI. BSD New (3-Clause) by default.
