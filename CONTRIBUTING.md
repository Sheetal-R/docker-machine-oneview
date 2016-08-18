# Contributing to Docker

Want to hack on docker-machine-oneview? Awesome!  
Our contribution model follows closely with the Docker contribution model
because this project targets to work with https://github.com/docker/machine
project work.   Please see read the [docker contribution](https://github.com/docker/docker/blob/master/CONTRIBUTING.md) model first.

![Contributors guide](docs/static_files/contributors.png)

## Topics

* [Building](#building)
* [Reporting Issues](#reporting-other-issues)
* [Quick Contribution Tips and Guidelines](#quick-contribution-tips-and-guidelines)
* [Community Guidelines](#docker-community-guidelines)

# Building

The requirements to build Machine are:

1. A running instance of Docker or a Golang 1.5 development environment
   If you are not using docker for build, you must set enviroment option
   `USE_CONTAINER=false`.  Otherwise most targets will build with docker.
2. The `bash` shell
3. [Make](https://www.gnu.org/software/make/)
4. When building dependencies with target `make glide` you will need go and glide
   installed.

## Build using Docker containers

To build the `docker-machine` binary, simply run:

```
    $ make build
```

## Built binary

After the build is complete a `bin/docker-machine-driver-oneview` binary will be created.

You may call:

```
    $ make clean
```

to clean-up build results.

## Check, test and validation

To run basic validation (dco, fmt), and the project unit tests, call:

```
    $ make test
```

If you want more indepth validation (vet, lint), and all tests with race detection, call:

```
    $ make validate
```

If you want to simply check dco, fmt, or lint use:

```
    $ make check
```

If you make a pull request, it is highly encouraged that you submit tests for
the code that you have added or modified in the same pull request.

## Code Coverage

To generate an html code coverage report of the Machine codebase, run:

```
    make coverage-serve
```

And navigate to http://localhost:8000 (hit `CTRL+C` to stop the server).

### Native build

Alternatively, if you are building natively, you can simply run:

```
    make coverage-html
```

This will generate and open the report file.

## List of all targets

### High-level targets

    make clean
    make build
    make test
    make validate

### Advanced build targets

Build for a specific list of oses and architectures:

    TARGET_OS=linux TARGET_ARCH="amd64 arm" make build

You can further control build options through the following environment variables:

    DEBUG=true # enable debug build
    STATIC=true # build static (note: when cross-compiling, the build is always static)
    VERBOSE=true # verbose output

### Tests targets

    make test-short
    make test-long
    make test-integration

### Validation targets

    make fmt
    make vet
    make lint
    make dco

# Reporting other issues

A great way to contribute to the project is to send a detailed report when you
encounter an issue. We always appreciate a well-written, thorough bug report,
and will thank you for it!

Check that [our issue database](https://github.com/Sheetal-R/docker-machine-oneview/issues)
doesn't already include that problem or suggestion before submitting an issue.
If you find a match, add a quick "+1" or "I have this problem too." Doing this
helps prioritize the most common problems and requests. **DO NOT DO THAT** to
subscribe to the issue unless you have something meaningful to add to the
conversation. The best way to subscribe the issue is by clicking Subscribe
button in top right of the page.

When reporting issues, please include your host OS (Ubuntu 12.04, Fedora 19,
etc). Please include:

* The output of `uname -a`.
* The output of `docker version`.
* The output of `docker info`.
* The output of `docker-machine --version`.

Please also include the steps required to reproduce the problem if possible and
applicable. This information will help us review and fix your issue faster.

**Issue Report Template**:

```
Description of problem:


`docker version`:


`docker info`:

`docker-machine --version`:


`uname -a`:


Environment details :


How reproducible:


Steps to Reproduce:
1.
2.
3.


Actual Results:


Expected Results:


Additional info:



```


#Quick contribution tips and guidelines

This section gives the experienced contributor some tips and guidelines.

##Pull requests are always welcome

Not sure if that typo is worth a pull request? Found a bug and know how to fix
it? Do it! We will appreciate it. Any significant improvement should be
documented as [a GitHub issue](https://github.com/Sheetal-R/docker-machine-oneview/issues) before
anybody starts working on it.

## Conventions

Fork the repository and make changes on your fork in a feature branch:

- If it's a bug fix branch, name it XXXX-something where XXXX is the number of
	the issue.
- If it's a feature branch, create an enhancement issue to announce
	your intentions, and name it XXXX-something where XXXX is the number of the
	issue.

Submit unit tests for your changes. Go has a great test framework built in; use
it! Take a look at existing tests for inspiration. [Run the full test
suite](https://docs.docker.com/project/test-and-docs/) on your branch before
submitting a pull request.

Update the documentation when creating or modifying features. Test your
documentation changes for clarity, concision, and correctness, as well as a
clean documentation build. See our contributors guide for [our style
guide](https://docs.docker.com/project/doc-style) and instructions on [building
the documentation](https://docs.docker.com/project/test-and-docs/#build-and-test-the-documentation).

Write clean code. Universally formatted code promotes ease of writing, reading,
and maintenance. Always run `gofmt -s -w file.go` on each changed file before
committing your changes. Most editors have plug-ins that do this automatically.

Pull request descriptions should be as clear as possible and include a reference
to all the issues that they address.

Commit messages must start with a capitalized and short summary (max. 50 chars)
written in the imperative, followed by an optional, more detailed explanatory
text which is separated from the summary by an empty line.

Code review comments may be added to your pull request. Discuss, then make the
suggested modifications and push additional commits to your feature branch. Post
a comment after pushing. New commits show up in the pull request automatically,
but the reviewers are notified only when you comment.

Pull requests must be cleanly rebased on top of master without multiple branches
mixed into the PR.

**Git tip**: If your PR no longer merges cleanly, use `rebase master` in your
feature branch to update your pull request rather than `merge master`.

Before you make a pull request, squash your commits into logical units of work
using `git rebase -i` and `git push -f`. A logical unit of work is a consistent
set of patches that should be reviewed together: for example, upgrading the
version of a vendored dependency and taking advantage of its now available new
feature constitute two separate units of work. Implementing a new function and
calling it in another file constitute a single logical unit of work. The very
high majority of submissions should have a single commit, so if in doubt: squash
down to one.

After every commit, [make sure the test suite passes]
(https://docs.docker.com/project/test-and-docs/). Include documentation
changes in the same pull request so that a revert would remove all traces of
the feature or fix.

Include an issue reference like `Closes #XXXX` or `Fixes #XXXX` in commits that
close an issue. Including references automatically closes the issue on a merge.

Please do not add yourself to the `AUTHORS` file, as it is regenerated regularly
from the Git history.

Please see the [Coding Style](#coding-style) for further guidelines.

## Merge approval

Project maintainers use LGTM (Looks Good To Me) in comments on the code review to
indicate acceptance.

A change requires LGTMs from an absolute majority of the maintainers of each
component affected. For example, if a change affects `docs/` and `registry/`, it
needs an absolute majority from the maintainers of `docs/` AND, separately, an
absolute majority of the maintainers of `registry/`.

For more details, see the [MAINTAINERS](MAINTAINERS) page.

## Sign your work

The sign-off is a simple line at the end of the explanation for the patch. Your
signature certifies that you wrote the patch or otherwise have the right to pass
it on as an open-source patch. The rules are pretty simple: if you can certify
the below (from [developercertificate.org](http://developercertificate.org/)):

```
Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
660 York Street, Suite 102,
San Francisco, CA 94110 USA

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.

Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.
```

Then you just add a line to every git commit message:

    Signed-off-by: Joe Smith <joe.smith@email.com>

Use your real name (sorry, no pseudonyms or anonymous contributions.)

If you set your `user.name` and `user.email` git configs, you can sign your
commit automatically with `git commit -s`.

Note that the old-style `Docker-DCO-1.1-Signed-off-by: ...` format is still
accepted, so there is no need to update outstanding pull requests to the new
format right away, but please do adjust your processes for future contributions.

# Docker community guidelines

We want to keep the Docker community awesome, growing and collaborative. We need
your help to keep it that way. To help with this we've come up with some general
guidelines for the community as a whole:

* Be nice: Be courteous, respectful and polite to fellow community members:
  no regional, racial, gender, or other abuse will be tolerated. We like
  nice people way better than mean ones!

* Encourage diversity and participation: Make everyone in our community feel
  welcome, regardless of their background and the extent of their
  contributions, and do everything possible to encourage participation in
  our community.

* Keep it legal: Basically, don't get us in trouble. Share only content that
  you own, do not share private or sensitive information, and don't break
  the law.

* Stay on topic: Make sure that you are posting to the correct channel and
  avoid off-topic discussions. Remember when you update an issue or respond
  to an email you are potentially sending to a large number of people. Please
  consider this before you update. Also remember that nobody likes spam.

## Guideline violations — 3 strikes method

The point of this section is not to find opportunities to punish people, but we
do need a fair way to deal with people who are making our community suck.

1. First occurrence: We'll give you a friendly, but public reminder that the
   behavior is inappropriate according to our guidelines.

2. Second occurrence: We will send you a private message with a warning that
   any additional violations will result in removal from the community.

3. Third occurrence: Depending on the violation, we may need to delete or ban
   your account.

**Notes:**

* Obvious spammers are banned on first occurrence. If we don't do this, we'll
  have spam all over the place.

* Violations are forgiven after 6 months of good behavior, and we won't hold a
  grudge.

* People who commit minor infractions will get some education, rather than
  hammering them in the 3 strikes process.

* The rules apply equally to everyone in the community, no matter how much
	you've contributed.

* Extreme violations of a threatening, abusive, destructive or illegal nature
	will be addressed immediately and are not subject to 3 strikes or forgiveness.

* Contact abuse@docker.com to report abuse or appeal violations. In the case of
	appeals, we know that mistakes happen, and we'll work with you to come up with a
	fair solution if there has been a misunderstanding.

# Coding Style

Unless explicitly stated, we follow all coding guidelines from the Go
community. While some of these standards may seem arbitrary, they somehow seem
to result in a solid, consistent codebase.

It is possible that the code base does not currently comply with these
guidelines. We are not looking for a massive PR that fixes this, since that
goes against the spirit of the guidelines. All new contributions should make a
best effort to clean up and make the code base better than they left it.
Obviously, apply your best judgement. Remember, the goal here is to make the
code base easier for humans to navigate and understand. Always keep that in
mind when nudging others to comply.

The rules:

1. All code should be formatted with `gofmt -s`.
2. All code should pass the default levels of
   [`golint`](https://github.com/golang/lint).
3. All code should follow the guidelines covered in [Effective
   Go](http://golang.org/doc/effective_go.html) and [Go Code Review
   Comments](https://github.com/golang/go/wiki/CodeReviewComments).
4. Comment the code. Tell us the why, the history and the context.
5. Document _all_ declarations and methods, even private ones. Declare
   expectations, caveats and anything else that may be important. If a type
   gets exported, having the comments already there will ensure it's ready.
6. Variable name length should be proportional to it's context and no longer.
   `noCommaALongVariableNameLikeThisIsNotMoreClearWhenASimpleCommentWouldDo`.
   In practice, short methods will have short variable names and globals will
   have longer names.
7. No underscores in package names. If you need a compound name, step back,
   and re-examine why you need a compound name. If you still think you need a
   compound name, lose the underscore.
8. No utils or helpers packages. If a function is not general enough to
   warrant it's own package, it has not been written generally enough to be a
   part of a util package. Just leave it unexported and well-documented.
9. All tests should run with `go test` and outside tooling should not be
   required. No, we don't need another unit testing framework. Assertion
   packages are acceptable if they provide _real_ incremental value.
10. Even though we call these "rules" above, they are actually just
    guidelines. Since you've read all the rules, you now know that.

If you are having trouble getting into the mood of idiomatic Go, we recommend
reading through [Effective Go](http://golang.org/doc/effective_go.html). The
[Go Blog](http://blog.golang.org/) is also a great resource. Drinking the
kool-aid is a lot easier than going thirsty.
