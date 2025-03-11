# 🚀 Hands-On Git Rebase Example

## Step 1: Set Up a Test Repository

If you don’t have one already, create a test repo:

```bash
mkdir git-rebase-demo
cd git-rebase-demo
git init
```

Create an initial main branch:

```bash
echo "Hello from main" > file.txt
git add file.txt
git commit -m "Initial commit on main"
```

Now, push it to GitHub (optional):

```bash
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main
```

## Step 2: Create and Work on a Feature Branch

Create a feature branch and add some commits:

```bash
git checkout -b feature-branch
echo "Feature work 1" >> file.txt
git add file.txt
git commit -m "Feature commit 1"

echo "Feature work 2" >> file.txt
git add file.txt
git commit -m "Feature commit 2"
```

Your history looks like this:

```bash
main:      A---B
               \
feature:        C---D  (your commits)
```

## Step 3: Update main (Simulating a Team Update)

Switch back to main and simulate another team member adding changes:

```bash
git checkout main
echo "New update on main" >> file.txt
git add file.txt
git commit -m "Another commit on main"
```

```bash
main:      A---B---E  (New commit in main)
               \
feature:        C---D  (Your commits)
```

At this point, feature-branch is behind main, so we need to rebase.

## Step 4: Rebase feature-branch Onto main

Now, rebase your feature branch to get the latest updates:

```bash
git checkout feature-branch
git rebase main
```

What Happens?
• Git moves your commits (C, D) and applies them on top of main.
• The new commit history will look like:

```bash
main:      A---B---E
                   \
feature (rebased):  C'---D'  (Replayed commits on top of main)
```

## Step 5: Handle Merge Conflicts (If Any)

If there’s a conflict, Git will pause the rebase and ask you to resolve it.

1. See which files have conflicts: `git status`
2. Open the conflicted file (file.txt) and manually fix the conflict.
3. Mark it as resolved:

```bash
git add file.txt
git rebase --continue
```

4. If you ever want to abort the rebase: `git rebase --abort`

## Step 6: Push Your Changes

After a successful rebase, push the updated branch:
`git push origin feature-branch --force`

Final Notes

✅ You have successfully rebased!
✅ Your commits now appear on top of main.
✅ No unnecessary merge commits were added.
✅ Your branch is now up-to-date with main.

##

```bash

```
