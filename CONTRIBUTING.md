# Contributing to e-SAFE Android application

Want to hack on e-SAFE Android? Awesome!
Here are instructions to get you started.
They are probably not perfect, please let us know if anything feels wrong or incomplete.

## Reporting Issues

Please report [Android specific issues here](https://github.com/openhab/openhab-android/issues).

## Build Environment

For instructions on setting up your development environment, please see [README](https://github.com/openhab/openhab-android/blob/main/README.md).

## Contribution guidelines

### Pull requests are always welcome

We are always thrilled to receive pull requests, and do our best to process them as fast as possible.
Not sure if that typo is worth a pull request? Do it! We will appreciate it.

If your pull request is not accepted on the first try, don't be discouraged!
If there's a problem with the implementation, hopefully you received feedback on what to improve.

### Discuss your design on the community forum

We recommend discussing your plans on the [community forum](https://community.openhab.org) before starting to code - especially for more ambitious contributions.
This gives other contributors a chance to point you in the right direction, give feedback on your design, and maybe point out if someone else is working on the same thing.

### Create issues...

Any significant improvement should be documented as [a GitHub issue](https://github.com/openhab/openhab-android/labels/enhancement) before anybody starts working on it.

### ...but check for existing issues first!

Please take a moment to check that an issue doesn't already exist documenting your bug report or improvement proposal.
If it does, it never hurts to add a quick "+1" or "I have this problem too".
This will help prioritize the most common problems and requests.

### Conventions

Fork the repo and make changes on your fork in a feature branch:

- If it's a bug fix branch, name it XXX-something where XXX is the number of the issue
- If it's a feature branch, create an enhancement issue to announce your intentions, and name it XXX-something where XXX is the number of the issue.

Write clean code. Universally formatted code promotes ease of writing, reading, and maintenance.

Pull requests descriptions should be as clear as possible and include a reference to all the issues that they address.

Pull requests must not contain commits from other users or branches.

Commit messages must start with a capitalized and short summary (max. 50 chars) written in the imperative, followed by an optional, more detailed explanatory text which is separated from the summary by an empty line.

Code review comments may be added to your pull request.
Discuss, then make the suggested modifications and push additional commits to your feature branch.
Be sure to post a comment after pushing.
The new commits will show up in the pull request automatically, but the reviewers will not be notified unless you comment.

Before the pull request is merged, make sure that you squash your commits into logical units of work using `git rebase -i` and `git push -f`.
After every commit the test suite should be passing.
Include documentation changes in the same commit so that a revert would remove all traces of the feature or fix.

Commits that fix or close an issue should include a reference like `Closes #XXX` or `Fixes #XXX`, which will automatically close the issue when merged.

### Sign your work

The sign-off is a simple line at the end of the explanation for the patch, which certifies that you wrote it or otherwise have the right to pass it on as an open-source patch.
The rules are pretty simple: if you can certify the below (from [developercertificate.org](http://developercertificate.org/)):

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

then you just add a line to every git commit message or use `-s` when committing to add the line automatically:

    Signed-off-by: Joe Smith <joe.smith@email.com> (github: github_handle)

using your real name (sorry, no pseudonyms or anonymous contributions.)

#### Small patch exception

There are several exceptions to the signing requirement. Currently these are:

* Your patch fixes spelling or grammar errors.
* Your patch is a single line change to documentation.

## Community Guidelines

We want to keep the e-SAFE community awesome, growing and collaborative.
We need your help to keep it that way.
To help with this we've come up with some general guidelines for the community as a whole:

* Be nice: Be courteous, respectful and polite to fellow community members: no regional, racial, gender, or other abuse will be tolerated.
  We like nice people way better than mean ones!

* Encourage diversity and participation: Make everyone in our community feel welcome, regardless of their background and the extent of their contributions, and do everything possible to encourage participation in our community.

* Keep it legal: Basically, don't get us in trouble.
  Share only content that you own, do not share private or sensitive information, and don't break the law.

* Stay on topic: Make sure that you are posting to the correct channel and avoid off-topic discussions.
  Remember when you update an issue or respond to an email you are potentially sending to a large number of people.
  Please consider this before you update.
  Also remember that nobody likes spam.

## FAQ

**Is there an architectural design for the presentation layer?**

There is no MVVM/MVP or MVC in place, because the app is not too complex and it would not really benefit from something like that right now.

**Is there an architectural design for the data layer?**

The data layer is separated to it's own package.

**Where does the Sitemap rendering happen?**

WidgetListFragment + (especially) WidgetAdapter

**How is navigation managed?**

ContentController manages how fragments are displayed, and MainActivity commands it what fragments to display.
Navigation is too dynamic in our app (determined by Sitemap) for the navigation architecture component to be useful.

**Do we use fragments in our activities? If yes, are they necessary?**

The answer to the first question is 'it depends'.
They should be used whenever it makes sense to use them.
E.g. for very simple activities like the LogActivity, we don't use fragments, otherwise we do.

**How can I add new "Send device information to server" Items?**

Just have a look at existing items, especially at the usage of the constants `PrefKeys.SEND_*`.
Battery level is a quite simple one without any permission checks (no permissions needed).
Reading the Wi-Fi SSID requires a permission, so check out that item if your item also requires a permission.

**Should my code be tested? If yes to which degree?**

Ideally yes, to whatever extent is doable and meaningful. It's not a requirement though.

**Is there a way I can test all the features against a test server or something similar?**

Either test against the [demo server](https://demo.openhab.org), or setup an own server.
For the latter case, it's probably useful to do a checkout of the server side code an run that, following the procedure in https://www.openhab.org/docs/developer/#setup-the-development-environment

**Do we have guidelines for code style?**

Yes, Android Kotlin Style Guide:
https://developer.android.com/kotlin/style-guide

In addition: Please omit " e-SAFE " or "My" from class names.

**How does the CI/CD pipeline work?**

Service | Shown as | Task | Desired result | How to fix
:----|:----|:----|:----|:----
GitHub Action | Build App | Runs full build and unit test suite | Must pass | Look at the check output and try to run the test locally.
Stickler CI | stickler-ci | Runs ktlint to ensure the Kotlin Style Guide is followed | Must pass | Look at the check output.
GitHub Action | Validate strings | Checks for common mistakes in strings.xml, e.g. wrong spelling of " e-SAFE " | Must pass | Look at the check output.
Developer Certificate of Origin | DCO | Checks if commits are signed-of-by | Must pass | `git commit -s --amed` and `git push -f`
WIP | WIP | Checks if the PR name contains "WIP" (Work in progress) | Must pass | Remove "WIP" from the PR title when you're done.

**Do I have to include Java Doc?**

It's always nice to see documentation, but as long as your code is clean, it is not all that important.
