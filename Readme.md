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
