# How to contribute to OpenSSL

For general ideas about how to contribute please have a look at the article 
[Getting Started as a contributor](
https://www.openssl.org/community/getting-started.html) on our homepage. 
This page concentrates on you possibilites to contribute via GitHub.

All current Development is done on GitHub. The
[GitHub repository](https://github.com/openssl/openssl) is
a mirror of the main repository at 
[git.openssl.org](https://git.openssl.org), which is updated almost immediately
whenever new commits are pushed.

## Feature Requests and Bug Reports

To request new features or report bugs, please open an [issue](
https://github.com/openssl/openssl/issues). Before doing it,
try to enter keywords in the search bar of the issue list to find out whether
someone else might have created a similar issue already.

## Pull Request

To submit a patch, please open a [pull request](
https://github.com/openssl/openssl/pulls).  If you are thinking
of making a large contribution, open an issue for it before starting work,
to get comments from the community.  Someone may be already working on
the same thing or there may be reasons why that feature isn't implemented.

To make it easier to review and accept your pull request, please follow these
guidelines:

### Contributor License Agreement

Anything other than a trivial contribution requires a Contributor License Agreement(CLA),
giving us permission to use your code. See [Contributor Agreements](
https://www.openssl.org/policies/cla.html) for details.

Every pull request is automatically checked by our [cla-bot](
https://github.com/openssl-machine) which complains when the CLA is missing.

### Trivial Contributions

If your contribution is very small, you and the reviewers can agree that it
is a trivial change, in which case no CLA is required. Note however that the
bar for a non-trivial change is set very low. Only typographical or formatting errors
are considered trivial, as well as obvious fixes in a view lines.

To indicate that you think it is trivial, and to soothe the cla-bot, add the text
`CLA: trivial` as a separate line by itself, to the _body_ of the commit message,
i.e., separated from the commit title by an empty line, like so:

```
Fix some typos

CLA: trivial
```


### Copyright Notice

All _new_ source files need to start with the following text (with appropriate comment
characters at the start of each line and the year(s) updated):

```
    Copyright 20xx-20yy The OpenSSL Project Authors. All Rights Reserved.

    Licensed under the OpenSSL license (the "License").  You may not use
    this file except in compliance with the License.  You can obtain a copy
    in the file LICENSE in the source distribution or at
    https://www.openssl.org/source/license.html
```
	
The years of existing source files don't need to be updated manually. This is done
automatically during the release process for every file that has been modified.

The reviewers need to agree that it is trivial. Normally, the do it by stating something
like "I agree it's trivial" while reviewing or when approving.


### Be up to date

Patches should be based on the `master` branch and as current as possible.
If the patch is a bug fix which also applies to stable branches, then the
reviewers will decide whether it should be backported.

Only in exceptional cases pull requests against stable branches are accepted.
These exceptions include bug fixes which only apply to older branches or
the case when a commit on the `master` branch can't be cherry-picked without
conflicts. In that case, a separate pull request for the resolved patch needs
to be submitted.

When your patch becomes outdated and its changes conflict with the master branch,
it needs to be rebased. Don't merge master into your branch, we don't accept 
merged commits. If you do happen to do it (sometimes the web interface is quick
at merging), you need to undo the merge commit and rebase instead.


### Coding Style

Patches should follow our [coding style](
https://www.openssl.org/policies/codingstyle.html) and compile
without warnings. Where gcc or clang is available you should use the
`--strict-warnings` Configure option.  OpenSSL compiles on many varied
platforms: try to ensure you only use portable features.  Clean builds
via Travis and AppVeyor are required, and they are started automatically
whenever a pull request is created or updated.


### Tests

When at all possible, patches should include tests. These can
either be added to an existing test, or completely new.  Please see
[test/README](../test/README) for information on the test framework.

### Documentation

#### Manual Pages

New features or changed functionality must include documentation.
The OpenSSL manuals are created using [perldoc](https://perldoc.perl.org).
Please look at the pod-files in doc/man[1357] for examples of our style.
Run `make doc-nits` to make sure that your documentation changes are clean.

#### CHANGES

For user visible changes (API changes, behaviour changes, ...),
consider adding a note in [CHANGES](../CHANGES).  This could be a summarising
description of the change, and could explain the grander details.
Have a look through existing entries for inspiration. 
Please note that this is NOT simply a copy of git-log oneliners.
Also note that security fixes get an entry in CHANGES.
This file helps users get more in depth information of what comes
with a specific release without having to sift through the higher
noise ratio in git-log.

#### NEWS

For larger or more important user visible changes, as well as
security fixes, please add a line in [NEWS](../NEWS).  On exception,
it might be worth adding a multi-line entry (such as the entry that
announces all the types that became opaque with OpenSSL 1.1.0).
This file helps users get a very quick summary of what comes with a
specific release, to see if an upgrade is worth the effort.
