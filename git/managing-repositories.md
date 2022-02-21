---
layout: default
title: Managing Repositories
nav_order: 1
parent: Git
---

# Managing Repositories
{: .no_toc }

1. TOC
{:toc}

## Local Repositories

### Creating a Local Repository
Creating a new local repository is easy:

```bash
git init
git add <files>
git commit -m "Message here"
```

This will create a `master` branch.

### Deleting a Local Repository
If you want to delete only the **Git-related information**, delete the `.git` directory. If you want to delete **Git-related information** and all code, delete the directory.

In addition, if the repository is linked to a remote repository, you will need to delete that too.

## Remote Repositories

### Creating a Remote Repository (GitHub)

1. Create a new repository on [GitHub](https://github.com/) using the point-and-click interface. Copy the clone link e.g. `https://github.com/chrischow/repo-name.git`. Note that this will create a `main` branch.
2. Create a new local repository using the instructions above. Note that this will create a `main` branch.
3. In the local repo, move (`-m`) the `master` to the `main` branch:

    ```bash
    git branch -m master main
    ```

4. In the local repo, add the remote repo as the origin:

    ```bash
    git remote add origin https://github.com/chrischow/repo-name.git
    ```

5. Push:

    ```bash
    git push origin main
    ```

### Deleting a Remote Repository (GitHub)
1. Go to **Settings**.
2. Scroll all the way to the bottom. Under **Danger Zone**, select **Delete this repository**.
3. Type in the repo name.
4. Wave goodbye!

## Important Documents

### README File
It's always a good practice to add a README to explain what the repository contains, especially if the code is to be used by others. **Installation** and **usage** are an absolute must to help users get started. An **impetus/context** section is optional, but useful to paint the context.

### `.gitignore` File
Unless your project involves 100% public data, you will need to avoid pushing credentials to GitHub. Hence, it's best to create this file upfront to prepare for that possibility. It is dangerous to commit any sensitive files **even once**, because that file would exist in the repo's history.

## Managing Files to be Ignored
There may be cases where you have committed some files to GitHub, and only later on realising that you no longer want updates pushed, or the files put online. You then add the files to `.gitignore`. However, these files will still exist in the GitHub repo. To resolve this, we remove the files from the cache.

After you have added the required files to `.gitignore`, use the following:

```bash
git rm -r --cached <folders/files>
```

Commit the changes as per normal:

```bash
git add .
git commit -m "Removed files in .gitignore"
git push origin main
```