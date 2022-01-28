# neperfepx-git

##### Version 1.0.1-6

## Description

`neperfepx-git` is a script that replaces the usual `git` commit for Neper and FEPX development.  It runs `git` with the provided arguments and, depending on the argument, runs additional commands.  When the argument is `commit` or `merge`, the script also updates the version number and (for `merge`) helps to resolve merge conflicts. When the command is `mergepr` (which is specific to `neperfepx-git`), the script merges the remote branch associated to the pull request.

`neperfepx-git` automatically detects whether it is run from within a Neper or an FEPX repository, and behaves accordingly.  If it is run from outside of a Neper or FEPX repository, it behaves as the `git` command.  It can therefore be used safely anywhere, and it is a good idea to alias it as `git` to have it seamlessly used instead of the standard `git` command (the actual `git` command remains available as `\git`).  `neperfepx-git` therefore behaves differently from `git` only when called with arguments `commit`, `merge` or `mergepr`.

### neperfepx-git commit

What `neperfepx-git commit` does (chronologically) is to

- create the commit
- update the version number
- open the `VERSIONS` file for your to complete
- update the commit to include the updated version number and `VERSIONS` file

### neperfepx-git merge

What `neperfepx-git merge branch_name` does (chronologically) is to

- merge `branch_name`
- update the version number
- open `meld` for you to solve conflicts (if any)
- open the `VERSIONS` file for your to complete
- update the merge commit to include the updated version number and `VERSIONS` file

### neperfepx-git mergepr

What `neperfepx-git mergepr remote_repository/branch_name` does (chronologically) is to

- download objects from the remote repository (`git fetch`)
- merge `repository/branch_name` using `neperfepx-git merge`
- push the base branch to the remote repository (this closes the PR)
- remove `branch_name` from the local repository (if it exists)
- remove `branch_name` from the remote repository
- remove the reference to `remote_repository/branch_name` from the local repository

## Prerequisites

The `git` and `merge` commands must be available, and the `NEPERROOT` and `FEPXROOT` environment variables must be defined, which point to the root directories of the Neper and FEPX local repositories.

## Usage

The script is simply to be called as

```
  $ neperfepx-git [arguments]
```

## Installation

The script should be copied to a standard directory (which belongs to `$PATH`) to make it available system-wide and/or aliased as `git` by adding `alias git=path/to/neperfepx-git` to the `~/.bashrc` file.
