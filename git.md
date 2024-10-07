# Resources

- [git Reference](https://git-scm.com/docs)
- [GitHub git Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet/)
- [git Essentials](https://www.learnlinux.tv/git-essentials/)

# Beginning

The differentiating factor between a directory and a repository is the presence of the `.git` directory. To create a repository, either clone an existing repository or initialise an new one with the following commands:

```bash
git init <name>
git init --initial-branch=<branch-name>
git clone <url>
```

If no name is stated in the `git init` command, then the current working directory becomes the repository. If the `git clone` command is run, then a new directory is created in the current working directory with the repository.

# Branches

The name of the default branch is different based on the version of **git**. Commonly chosen names include 'main', 'development', and 'trunk'. To change the default branch to adhere to common practice, use the following command:

```bash
git branch -m <name>
git branch -m master main
```

# Status

Simply saving a file in a repository does not make it part of the repository. You can test this by adding a file to the repository and running the `git status` command. If your terminal has color coding, the newly added file will be printed in red. You must manually declare the file to be part of version control and add it to the current 'commit' with the command:

```bash
git add <file>
git add README.md
git add [--update | -u]
git add .
```

Then, after running `git status` again, the file will be printed in green and the terminal output states the changes will be committed. To note, the above applies to both new files, and updated files; for simplicity, the example only mentioned a new file.

To add all tracked files in the entire working tree, use the `-u` or `--update` flag. To add both tracked and untracked files, use `.`.

To view the changes in detail, run the following command:

```bash
git diff <file>
```

# Config

The `git config` command allows you to configure **git** on your machine. An important command is to set who is committing the changes to a repository, which is as follows:

```bash
git config --global user.name "Aydin Aksel"
git config --global user.email "aaydinaksel@gmail.com"
```

# Commit

Commit the changes made in the current commit. This includes everything that is tracked in the `git add` command.

```bash
git commit -m "<commit-message>"
git commit -m "Initial commit of README.md"
```

# Reverting Commit

Running `git log --online` displays all commits made to the default branch. The line in the terminal output containing `(Head -> main)` is the current version of the default branch. To revert to a previous commit, enter the following command:

```bash
git revert <commit-hash>
```

Important to note, the 'hash' you enter is not for the commit you want to revert to, but rather the commit you want to undo. After running the command, enter details for the reversion commit.

# Remote Repositories

To find the origin of a remote repository, you can run the following command and inspect the output:

```bash
cat .git/config
```

To push an existing repository to a remote, use the following command to associate the name `origin` with the `<url>`:

```bash
git remote add origin <url>
```

To alter the origin URL, use the command:

```bash
git remote set-url <url>
```

To send a commit to your remote, use the following command:

```bash
git push origin <branch-name>
```

# Pull from Remote

```bash
git pull
```

Updates your current local working branch with all new commits from the corresponding remote branch on GitHub. `git pull` is a combination of `git fetch` and `git merge`

# Safely Delete All Commits

1. Checkout/create orphan branch (this branch won't show in `git branch` command):
    
    ```bash
    git checkout --orphan latest_branch
    ```
    
2. Add all the files to the newly created branch:
    
    ```bash
    git add -A
    ```
    
3. Commit the changes:
    
    ```bash
    git commit -am "<commit-message>"
    ```
    
4. Delete default branch (this step is permanent):
    
    ```bash
    git branch -D <branch-name>
    ```
    
5. Rename the current branch to `main`:
    
    ```bash
    git branch -m main
    ```
    
6. Finally, all changes are completed on your local repository, and force update your remote repository:
    
    ```bash
    git push -f origin main
    ```