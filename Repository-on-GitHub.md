# Pushing a Folder to GitHub via VS Code Without Manually Creating the Repository on GitHub

## **Prerequisites**
Before proceeding, ensure you have the following installed:
- **Git**: [Download Git](https://git-scm.com/downloads) and install it.
- **GitHub CLI (gh)**: [Download GitHub CLI](https://cli.github.com/).
- **VS Code**: [Download VS Code](https://code.visualstudio.com/).

## **Step 1: Authenticate with GitHub in VS Code**
1. Open **VS Code Terminal** (`Ctrl + ~`).
2. Run the following command to log in to GitHub:
   ```sh
   gh auth login
   ```
3. Follow the authentication steps and authorize VS Code to access GitHub.

💡 *Example Output:*
```
? What account do you want to log into? GitHub.com
? How would you like to authenticate? Login with a web browser
```

---
## **Step 2: Navigate to Your Project Folder**
Use the terminal to move to your project directory:
```sh
cd path/to/your/project
```

💡 *Example:*
```sh
cd C:/Users/Mani/Documents/MyProject
```

---
## **Step 3: Initialize Git in the Project**
Run the following command to initialize Git in the project folder:
```sh
git init
```
💡 *This creates a hidden `.git` folder that tracks changes in your project.*

---
## **Step 4: Create a GitHub Repository Using GitHub CLI**
Run the following command:
```sh
gh repo create <repo-name> --public --source=. --remote=origin
```
💡 *Example:*
```sh
gh repo create myNewApp --public --source=. --remote=origin
```
Replace `<repo-name>` with your desired repository name.
- To create a **private** repository, use `--private` instead of `--public`.

📌 *If you see an error like below, proceed to the next step to fix it:*
```
X Unable to add remote "origin"
```

---
## **Step 5: Manually Add Remote (If Necessary)**
If the remote was not added, follow these steps:

1. **Check existing remotes:**
   ```sh
   git remote -v
   ```
   - If a remote named `origin` exists but is incorrect, remove it:
     ```sh
     git remote remove origin
     ```

2. **Add the correct remote manually:**
   ```sh
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   ```
   💡 *Example:*
   ```sh
   git remote add origin https://github.com/Manikanta1239/Python.git
   ```

3. **Verify the remote:**
   ```sh
   git remote -v
   ```
   Expected output:
   ```
   origin  https://github.com/Manikanta1239/Python.git (fetch)
   origin  https://github.com/Manikanta1239/Python.git (push)
   ```

---
## **Step 6: Push Your Code to GitHub**
1. **Add files to Git:**
   ```sh
   git add .
   ```
2. **Commit your changes:**
   ```sh
   git commit -m "Initial commit"
   ```
3. **Push to GitHub:**
   ```sh
   git push -u origin main
   ```
   *(If your branch is not named `main`, replace it with `master` or the correct branch name.)*

💡 *Example Output:*
```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (5/5), 500 bytes | 500.00 KiB/s, done.
To https://github.com/Manikanta1239/Python.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

---
## **Step 7: Change Branch from `master` to `main` (If Needed)**
If your default branch is `master` but you want to change it to `main`, follow these steps:

1. Rename the local branch:
   ```sh
   git branch -m master main
   ```
2. Push the renamed branch to GitHub:
   ```sh
   git push -u origin main
   ```
3. Change the default branch on GitHub (via the website):
   - Go to your repository on GitHub.
   - Navigate to **Settings > Branches**.
   - Change the default branch from `master` to `main`.
4. Delete the old `master` branch remotely:
   ```sh
   git push origin --delete master
   ```

---
## **Step 8: Confirm on GitHub**
Visit your GitHub repository at:
```
https://github.com/<your-username>/<repo-name>
```
💡 *Example:*
```
https://github.com/Manikanta1239/Python
```
Your code should now be uploaded! 🎉

---
## **Alternative: Using VS Code GUI (Without Terminal)**
1. Open VS Code and navigate to your project.
2. Open the **Source Control** panel (`Ctrl + Shift + G`).
3. Click **"Initialize Repository"**.
4. Click **"Publish to GitHub"**.
5. Follow the prompts to log in and create the repository.
6. Your code will automatically be pushed to GitHub.

---
## **Troubleshooting**
### 1. **Error: 'gh' is not recognized**
- Ensure GitHub CLI is installed and added to the system PATH.
- Restart VS Code after installing GitHub CLI.

### 2. **Permission denied (publickey)**
- Ensure you have set up SSH keys for GitHub: [GitHub SSH Guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys).
- Check if SSH authentication works by running:
  ```sh
  ssh -T git@github.com
  ```
  Expected output:
  ```
  Hi <your-username>! You've successfully authenticated, but GitHub does not provide shell access.
  ```

### 3. **Remote 'origin' already exists**
- Remove the existing remote:
  ```sh
  git remote remove origin
  ```
- Add the correct remote manually as shown in **Step 5**.

---
## **Conclusion**
You have successfully pushed your project to GitHub without manually creating the repository on the GitHub website. 🚀

If you have any issues, double-check the steps or run `git status` to debug.

Happy coding! 😃

