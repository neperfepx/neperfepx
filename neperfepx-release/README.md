# neperfepx-release

##### Version 1.0.1-6

## Description

`neperfepx-release` is a script to release new versions of Neper or FEPX.  It must be run from the Neper or FEPX directory. It creates a new release in several successive _stages_:

Local Git branch modifications, version updates and tests:

  1. Merging (squash) `devel` into `main` and updating the version number, 
     archiving `devel` as `devel-$oldversion`,
     creating a new `devel` starting from `main`, and
     creating a tag for the new version and a new start tag
  2. Running tests (src and doc compilation, ctest)
  3. Updating the website with the new version and its doc in `gh-pages`

Release _per se_:

  5. Pushing `main` and the new version tag to the public repository
  6. Pushing `main`, `devel`, `devel-$oldversion` and tags to the private repository
  7. Pushing the website (`gh-pages`)
  8. Making a new GitHub release on the public repository

## Prerequisites

As per Neper/FEPX's development workflow, in `$NEPERROOT` or `$FEPXROOT`, the Git remote repositories must be `github` (public) and `github-dev` (private).

## Usage

The scripts can then simply be called as

```
  $ neperfepx-release [start stage]
```

## Installation

The script should be copied to a standard directory (which belongs to `$PATH`) to make it available system-wide.
