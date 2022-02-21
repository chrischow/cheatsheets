---
layout: default
title: Create New Repository
nav_order: 1
parent: Git
---

# Create New Repository
{: .no_toc }

## Local Repository
Creating a new local repository is easy:

```bash
git init
git add <files>
git commit -m "Message here"
```

This will create a `master` branch.

## Remote Repository (GitHub)

1. Create a new repository on [GitHub](https://github.com/). Copy the clone link e.g. `https://github.com/chrischow/repo-name.git`. Note that this will create a `main` branch.
2. Create a new local repository using the instructions above. Note that this will create a `main` branch.
3. In the local repo, move (`-m`) the `master` to the `main` branch:

    ```bash
    git branch -m master main
    ```

4. In the local repo, add the remote repo as the origin:

    ```bash
    git remote add https://github.com/chrischow/repo-name.git
    ```

5. Push:

    ```bash
    git push origin main
    ```
