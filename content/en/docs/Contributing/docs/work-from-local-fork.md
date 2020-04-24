---
title:  "Work From a Local Fork"
linkTitle:  "Work From a Local Fork"
weight: 10
description: >
  Use git command line
---

Work from a local clone when you make changes that require multiple files, creating new files, changing the navigation, or moving files around. These instructions use the `git` command and assume that you have installed it locally.

# Clone the repository

You only need to clone the repository once per physical system where you work
on the documentation.

1. Create a fork of the `spinnaker/spinnaker.github.io`
repository on GitHub. In your web browser, go to
[spinnaker.github.io](https://github.com/spinnaker/spinnaker.github.io)
and click the **Fork** button. After a few seconds, you are redirected to the
URL for your fork, which is `https://github.com/<github_username>/spinnaker.github.io`.

1.  In a terminal window, use `git clone` to clone the your fork.

      ```bash
      git clone git@github.com/<github_username>/spinnaker.github.io
      ```

      The new directory `spinnaker.github.io` is created in your current
      directory, with the contents of your GitHub repository. Your fork is your
      `origin`.

1.  Change to the new `spinnaker.github.io` directory. Set the `spinnaker/spinnaker.github.io` repository as the `upstream` remote.

      ```bash
      cd website

      git remote add upstream https://github.com/spinnaker/spinnaker.github.io
      ```

1.  Confirm your `origin` and `upstream` repositories.

    ```bash
    git remote -v
    ```

    Output is similar to:

    ```bash
    origin	git@github.com:<github_username>/spinnaker.github.io.git (fetch)
    origin	git@github.com:<github_username>/spinnaker.github.io.git (push)
    upstream	https://github.com/spinnaker/spinnaker.github.io (fetch)
    upstream	https://github.com/spinnaker/spinnaker.github.io (push)
    ```

# Create a branch

1. You need to create a branch for your changes. Before creating your branch, make sure your local `origin` is up-to-date with `upstream`.

	```bash
	git fetch origin
	git fetch upstream
	```

	For documentation, you do not need to rebase your local copy of `master` with `upstream/master` and push to your fork because you will base your branch on the `upstream` repository. This is different from most code workflows.

1. Create a new branch

   ```bash
   git checkout -b <my-new-branch> upstream/master
   ```
    Note: you are basing your branch on the `upstream/master` repository; in other words, Git will track changes between your local repository and the upstream repository

# Work on changes and preview locally

Make changes using your favorite text editor or IDE. After you have finished, commit your changes to your branch.

1. Check which files you need to commit

	```bash
	git status
	```

	Output is similar to:

	```bash
	On branch <my-new-branch>
	Your branch is up to date with 'origin/<my-new-branch>'.

	Changes not staged for commit:
	(use "git add <file>..." to update what will be committed)
	(use "git checkout -- <file>..." to discard changes in working directory)

	modified:   community/contributing/docs/work-from-local-fork.md

	no changes added to commit (use "git add" and/or "git commit -a")
	```

1. Add the files listed under **Changes not staged for commit** to the commit:

    ```bash
    git add <your_file_name>
    ```

    Repeat this for each file.

1.  After adding all the files, create a commit:

    ```bash
    git commit -m "Your commit message"
    ```

    Do not use any [GitHub Keywords](https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword) in your commit message. You can add those to the pull request description later.

1. Push your local branch and its new commit to your remote fork:

    ```bash
    git push origin <my-new-branch>
    ```
