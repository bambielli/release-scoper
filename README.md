# release-scoper

A tool that examines git history between time.now() and the previous release on a branch, and pulls out the PR numbers.

### Background

We use the [git-flow](http://nvie.com/posts/a-successful-git-branching-model/) branching model at work. 

Procedurally, anything that enters the develop branch enters via a pull request that is peer reviewed and approved by the product owner.

Each commit on the devleop branch should therefore be a merge commit that merges a pull request (feature/work-item) in to the base branch. The format of these auto-generated commit messages is something like:

`Merge pull request #123 from org/branch-name`

Before cutting a release branch, the release owner examines the history between the previous release and the current state of develop and develops a list of the pull requests that are in scope for the next release candidate. These PR numbers are linked in the pull request that is opened for the release candidate, to communicate what is going out in this release version.

This tool aims to automate the manual task described above, by examining git logs on develop between the previous release and time.now(), to determine which pull requests are within the scope of the release.

### Requirements

#### Precondition

- User shall have minimally read access to the git repository for which the release-scope will be generated.

#### Features

- User shall be able to generate a list of pull requests and branch names that are within scope for the next release.
- User shall be able to optionally generate a pull request with the release scope populated in their org repository
  - Pull request shall include PR numbers in scope, and corresponding branch names.

