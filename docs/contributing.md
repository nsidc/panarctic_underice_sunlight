# Contributing

> **Note**
> Much of this guide is based on the [`xarray` contributing guide](https://docs.xarray.dev/en/stable/contributing.html)

## Where to start?

All contributions are welcome: bug reports, bug fixes, documentation improvements, enhancements, and ideas.

Please look at the "issues" tab first, to see if someone else has found a similar bug or suggested enhancement.

## Working with the code

### Getting started with Git

[GitHub has instructions](https://help.github.com/set-up-git-redirect) for installing git, setting up your SSH key,
and configuring git. All these steps need to be completed before you
can work seamlessly between your local repository and GitHub.

### Forking

You will need your own fork to work on the code. Go to the [project
page](https://github.com/nsidc/panarctic_underice_sunlight) and hit
the Fork button, which is at the top of the repo page. This creates a
copy of the repo under your own GitHub user.  Now you can clone your
fork to your machine:

```
git clone git@github.com:your-github-username/panarctic_underice_sunlight.git
cd panarctic_underice_sunlight
git remote add upstream git@github.com:nsidc/panarctic_underice_sunlight.git
```

This clones your fork of the repo and sets the origial repo as the upstream remote repository.


### Create the environment

It is recommended to create a new environment.  This keeps versions of
packages separate and avoid (to some extent) confusion and
frustration.

```
conda env create -f environment.yml

conda activate panarctic_underice_sunlight

# For older versions of conda
source activate panarctic_underice_sunlight
```

### Creating a branch

Your main branch should reflect only production-ready code.  This way,
you always have a working version of the code.  Before making changes,
create a feature branch. For example:

```
git branch shiny-new-feature
git checkout shiny-new-feature
```
The above can be simplified to:
```
git checkout -b shiny-new-feature
```

This changes your working directory to the shiny-new-feature
branch. Keep any changes in this branch specific to one bug or feature
so it is clear what the branch brings to xarray. You can have many
“shiny-new-features” and switch in between them using the git checkout
command.

To update this branch, you need to retrieve the changes from the main branch:

git fetch upstream
git merge upstream/main

This will combine your commits with the latest xarray git main. If
this leads to merge conflicts, you must resolve these before
submitting your pull request. If you have uncommitted changes, you
will need to git stash them prior to updating. This will effectively
store your changes, which can be reapplied after updating.

### Contributing changes

```
git status

git add path/to/file-to-be-added.py
git commit -m 'some commit message'
git push origin shiny-new-feature
```

### Updating the environment
**This is only necessary if we are making big changes**

If you need to add a new package or update a package specification, use the following workflow.

- Add a new entry to `environment.yml` using compatible release spec ~=
- `conda env update` to update your current environment with the new entry.
- `conda env export > environment-lock.yml` to save your exact working environment every time you make a change.
- If everything is working add, commit and push the new `environment.yml` and `environment-lock.yml`. 

**If you remove packages**, you may as well nuke your conda environment and recreate it from environment.yml fresh! (conda env create)
