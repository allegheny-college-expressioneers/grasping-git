# Grasping Git

So far in Computational Expression, you have used Git for:

- Copying, or `clone`ing, an assignment to JupyterLab
- Tracking, or `add`ing and `commit`ing, changes on JupyterLab
- Submitting, or `push`ing, changes from JupyterLab to GitHub

Although cloning and pushing are essential Git operations that you will need to perform for every assignment, you will spend most of your time tracking your changes through adding and committing in Git repositories. Coincidentally, tracking changes also tends to be the most confusing Git operation for those who are new to Git. Today, you will focus on the process of tracking your changes.

## `git status`: Display changes

Before tracking your changes, you need to know **what** changes exist in your repository.

If you have just cloned this repository and you run `git status`, you should see:

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

Line by line, this means:

- `On branch main`: You are currently on the main branch. You do not need to know about Git branching for now.
- `Your branch is up to date with 'origin/main'.`: All of the commits in your JupyterLab repository also exist in your GitHub repository.
- `nothing to commit, working tree clean`: You do not have any changes since the last commit.

This is because you have not yet made any changes. A change is any one of:

1. Adding a line to a file
1. Deleting a line from a file
1. Modifying a line in a file
1. Creating a file
1. Deleting a file
1. Renaming a file

Make a change by adding a line to a file, `deliverables/writing/reflection.md`.
Now, run `git status`.

```text
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   deliverables/writing/reflection.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Under `Changes not staged for commit`, you see that you have modified the `deliverables/writing/reflection.md` file.

What about when you create a file? Create a file, `deliverables/src/hello_me.py`, that contains a print statement. Run `git status`.

```text
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   deliverables/writing/reflection.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        deliverables/src/hello_me.py

no changes added to commit (use "git add" and/or "git commit -a")
```

Instead of appearing under `Changes not staged for commit`, the `hello_me.py` file appears under `Untracked files`. Untracked files are named as such because Git has never tracked changes in them before (which makes sense since you just created the file!).

At this point, you have two changes in your repository that you would like to track.

## `git add`: Add changes to commit

Now, run `git commit`. You should see the same output as before, which ends in `no changes added to commit`. Remember that a commit has two parts--the changes you want to track and a description of those changes. You can think of a commit as a "declaration" of a change in your repository.

"I have made these changes! And these changes are..."

So, to say

"I have added a line to `reflection.md`! This change is an answer to a reflection question."

you first need to add the changes in `reflection.md` to the commit.

Why not say,

"I have added a line to `reflected.md` and added a file called `hello_me.py`! These changes are an answer to a reflection question and the creation of a file."

? Because you want your commits to be **focused**--to encompass only one change to your repository. This change can span multiple **files** (e.g. fixing typos across multiple Markdown documents), but it should only be one change to your **repository** ("Fix typos").

Press pause for a second. Do you remember how in Groundwork Lab, you were instructed to run `git add .`, which added all of the changes in the current, or working, directory (`.`)? In actuality, you almost never use this command. 😲

Instead, you almost always specify the exact files that contain the changes you want to commit. But, this takes way more time! Why should you do this? Look again at the changes you have using `git status`. If you were to run `git add .`, you would add both `reflection.md` and `hello_me.py` to the commit. But, since you want to keep your commit focused, you only want to add `reflection.md`. You *could* delete `hello_me.py` before running `git add .` and create `hello_me.py` again. But, it is much easier to simply specify which file(s) you want to include in the commit.

So, run `git add deliverables/writing/reflection.md`. When you run `git status`, you should now see:

```text
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   deliverables/writing/reflection.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        deliverables/src/hello_me.py
```

Notice that `reflection.md` has moved from `Changes not staged for commit` to `Changes to be committed`. You have just said, "I have added a line to `reflection.md`! But, you have not finished "declaring" this change--you need to give a description of your change.

## `git commit -m`: Describe change and create commit

To do so, run `git commit -m "Answer reflection question."`. This command will both create a commit and attach the message you provided to that commit. If you successfully made a commit, you should see something like:

```text
[main 9fd85f3] Answer reflection question
...
```

By the way, did you notice the imperative mood of the commit message? This is best practice because commit messages need to be short and using the imperative mood saves a few characters. No, seriously.

Run `git status` again.

```text
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        deliverables/src/hello_me.py

no changes added to commit (use "git add" and/or "git commit -a")
```

Notice that it no longer says, `Your branch is up to date with 'origin/main'.`, but instead says, `Your branch is ahead of 'origin/main' by 1 commit.`? This indicates that you have one commit (the one you just made!) that you have not yet pushed to GitHub.

**Try adding and committing the `hello_me.py` file, with a commit message that reads, "Add hello_me.py file". Is the process any different from tracking the change in `reflection.md`?**

## `git log`: Display commits (i.e. version history)

`git log` will show you a list of your commits:

```text
commit 0ed06dde9acab9ecd9b1f3de0bc979a3e035aacf (HEAD -> main)
Author: Maria Kim Heinert <yeeunmariakim@gmail.com>
Date:   Fri Sep 3 05:52:44 2021 -0400

    Add hello_me.py file

commit 60f94a8dd598602a470b8a18aa932e975f613de5
Author: Maria Kim Heinert <yeeunmariakim@gmail.com>
Date:   Fri Sep 3 05:33:37 2021 -0400

    Answer reflection question

commit 57fe19858967cb42683da8f3750963e03c53bbc4 (origin/main)
Author: Maria Kim Heinert <yeeunmariakim@gmail.com>
Date:   Fri Sep 3 04:34:37 2021 -0400

    Add Hello, World! program
```

The last commit on GitHub is indicated by `origin/main`. You can see that this is *not* the last commit you made (`Add hello_me.py file`) on JupyterLab. This means that you have not yet pushed all your commits to GitHub--in other words, when I look at your GitHub repository, I will not see your latest work.

To push all of your commits to your GitHub repository, run `git push`. If you run `git log` again, you will see `origin/main` next to the latest commit on JupyterLab. You have successfully pushed all of your commits!

## Extra, extra!

**How do you track the renaming of a file?**

**What does the `.gitignore` file do?**
