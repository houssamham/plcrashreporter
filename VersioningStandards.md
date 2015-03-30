# Introduction #

We follow a fairly simple and standard branching, tagging, and versioning policy.

## Versioning ##

We use the standard major.minor.revision versioning approach. Note that as a rule, we try to avoid breaking API/ABI at all, and doing so should only be done if no other solution is available.

  * Major versions are incremented for significant changes/additions, including API/ABI-breaking changes.
  * Minor versions are incremented for API-compatible changes, including smaller feature releases.
  * Revisions are incremented for low-risk bug fix releases that resolve significant breaking changes in a stable release.

In addition to the above, we use the following designators for pre-release versions:

  * alpha (eg, 1.0-alpha1): Known-unstable alpha release.
  * beta (eg, 1.0-beta1): Possibly unstable beta release.
  * rc (eg, 1.0-rc1): Stable release candidate. Code tagged as a release candidate will ship as the final release version, unless a bug is found during RC testing.

## Release Tags ##

Each release is tagged in git with a version, as defined in the versioning rules above. Examples:

  * 1.0-beta1 -> 1.0-beta2 -> 1.0-rc1 -> 1.0-rc2 -> 1.0
  * 1.2.1-beta1 -> 1.2.1-beta2 -> 1.2.1-rc1 -> 1.2.1-rc2 -> 1.0

Depending on the size and scope of the changes, it may not be necessary to provide 'beta' designated releases for testing, but **all** releases must be provided as release candidates for user testing before being marked as a stable releases.

## Release Branches ##

Release branches are created on-demand from release tags (see above), and are used to track low-risk bug fixes to a given major.minor revision. The release branch will be named with the project prefix followed by the major.minor version of the release it is tracking, eg, plcrashreporter-`<`major`>`.`<`minor`>`.

## HEAD / Master ##

The HEAD (or 'master') branch tracks current development state of the project, including changes that have seen only limited testing. Commits made to this branch may not be sufficiently tested for release, but they must be in a presumed-stable state, and must include unit test coverage and API documentation.

Commits made to master _should not_ introduce breaking changes to file formats or encodings. Those changes should be considered, discussed, and approved on an issue-specific feature branch (see below).

## Feature Branches ##

Feature branches are used to track in-progress development of features (or bug fixes) that may have a destabilizing effect on the code base, cases where APIs may not yet be finalized, or potentially breaking changes to serialization formats.

While the requirements for feature branches are not quite as rigorous as master, you should still take care to commit stable and unit tested code (use TDD!). Bugs you don't implement are bugs you don't have to find later, and our test-driven approach is intended to minimize the number of bugs that occur, even on feature development branches.

Feature branches should be named as follows: `<`username`>`-`[`issue #`]`-`<`descriptive name`>`

For example:
  * landonf-54-addr-remap
  * landonf-mach-exceptions

As a general rule, branches should have associated issues attached to them. In practice -- especially with development spread across several issue trackers and organizations -- this may not be viable.

TODO: Revisit the issue tracker question. It would be preferable to have all issues be tracked in a central, public location, and for all commits to reference the specific issues they are tracking.

## Git Rebasing and Pushing ##

Git does a fantastic job of tracking revisions across branches, which is why we use it. What it doesn't always do a fantastic job of is in facilitating rapid communication between developers by providing sufficient visibility of individual changes. When working on PLCrashReporter:

  * Push early, push often. Create a feature branch if you're worried about destabilizing master.
  * Squashing commits discards useful history that provides insight into the process of developing an individual feature. **Don't do it.**