# Grasping Git

So far in Computational Expression, you have used Git for:

- Copying, or `clone`ing, an assignment to JupyterLab
- Tracking, or `add`ing and `commit`ing, changes on JupyterLab
- Submitting, or `push`ing, changes from JupyterLab to GitHub

Although cloning and pushing are essential Git operations that you will need to perform for every assignment, you will spend most of your time tracking your changes through adding and committing in Git repositories. Coincidentally, tracking changes also tends to be the most confusing Git operation for those who are new to Git. Today, let's focus on the process of tracking your changes.

## `git status`: Display changes

Before tracking your changes, you need to know **what** changes exist in your repository.

If you have just cloned this Git repository and you run `git status`, you should see:

```text

```

This is because you have not yet made any changes. A change is any one of:

1. Adding a line to a file
1. Deleting a line from a file
1. Modifying a line in a file
1. Creating a file
1. Deleting a file
1. Renaming a file

Let's add a line to a file, `deliverables/writing/reflection.md`, and then run `git status`.

```text

```

