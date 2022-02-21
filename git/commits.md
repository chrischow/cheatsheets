---
layout: default
title: Commits
nav_order: 2
parent: Git
---

# Commits
{: .no_toc }

1. TOC
{:toc}

## Making Commits
1. It is a good practice to check what files in your local repo were changed. This gives you the opportunity to think through how you can group the changes logically.

    ```bash
    git status
    ```

2. Stage files to be committed:

    ```bash
    # For adding ALL changes
    git add .

    # For adding specific files/folders
    git add <file name/folder name>
    ```

3. Commit the files and input a commit message.

    ```bash
    # Use inline comments for quick commits
    git commit -m "Message here"

    # Use nano for longer commit messages
    git commit
    ```

## Best Practices for Writing Commit Messages
For more substantial commits, it is a good practice to use a text editor like nano or vim to type out comments.

The format as recommended [here](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html) is:

```
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent

If you use an issue tracker, add a reference(s) to them at the bottom,
like so:

Resolves: #123
```