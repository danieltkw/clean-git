


# 🧹 Git History Cleaner for Multiple Repositories

This Bash script automates the process of resetting Git history for multiple repositories in a folder. It ensures each repo has only one clean commit and pushes it to GitHub.

## 📂 What It Does

- Loops through each subdirectory in the current folder.
- Checks if Git is initialized:
  - If yes: removes history and keeps only the latest commit.
  - If not: initializes Git and makes a clean commit.
- Force-pushes the cleaned repo to GitHub under `https://github.com/danieltkw/<repo-name>.git`.
- Second part of the script lists the current number of commits in each Git repo for verification.

## 🛠️ Requirements

- Bash shell (Linux/macOS or Git Bash on Windows)
- Git CLI
- GitHub credentials (either via SSH or stored credentials for HTTPS push)

## 🚀 Usage

1. Place this script in the parent folder containing all your repositories as subfolders.
2. Make it executable:

```bash
chmod +x clean_repos.sh

## This will permanently delete Git history in each repository and force-push over the remote. Use with caution.

