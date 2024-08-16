---
title : "Project Management"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 3.4 </b> "
---

## Project management using Git

#### Step 1: Install Git
Download and install **Git** here: [Git_Install](https://git-scm.com/).


#### Step 2: Config Git
1. Open **Git Bash**
2. Config **user name** and **email**
    ```
    git config --global user.name "User Name"
    ```
    ```
    git config --global user.email "username@gmail.com"
    ```
![Git_Config](/Dung_aws/images/3.4/0001.png)

3. Check config
    ```
    git config --global user.name
    ```
    ```
    git config --global user.email
    ```
![Git_Config](/Dung_aws/images/3.4/0002.png)


#### Step 3: Initialize repository
1. Make a new direction for the project and move into that direction
    ```
    mkdir <direction_name>
    ```
- **mkdir** stands for "make directory".
- **direction_name** is the name of the folder.
- This command will make a new direction named **direction_name** in the current direction.
    ```
    cd <direction_name>
    ```
- **cd** stands for "change directory".
- **direction_name** is the name of the folder you want to move into.
- This command will change your current direction to **direction_name**.

![Git_Initialize](/Dung_aws/images/3.4/0003.png)

2. Initialize **Repository**
    ```
    git init
    ```
- After running this command, Git will initialize a new repository in your current direction.
- This involves creating a hidden .git directory containing all the files needed to track changes in the project.
![Git_Initialize](/Dung_aws/images/3.4/0004.png)

3. Check status
    ```
    git status
    ``` 
- This command will show the current status of the repository, including which files have been changed but not committed yet.


#### Step 4: Add and Commit Change
This step involves creating a **README.md** file, adding content to it, and then adding the file to the Git staging area and committing the changes to your repository.

1. Create a **README.md** file and write a few lines describing the project:
- Make sure you are in the project directory.
- Use the **echo** command to create a README.md file and add a description line to it:
    ```
    echo "# AdvancedGitProject" >> README.md
    ```
This command will create a README.md file and add the line "#AdvancedGitProject" to it.

![Git](/Dung_aws/images/3.4/0005.png)

2. Check the contents of the **README.md** file:
    ```
    cat README.md
    ```
3. Add the **README.md** file to the staging area
- Use the **git add** command to add the README.md file to the staging area, preparing for commit:
    ```
    git add README.md
    ```
4. Commit change
- Use the **git commit** command to commit changes with a descriptive message:
    ```
    git commit -m "Add README.md with project description"
    ```

![Git](/Dung_aws/images/3.4/0006.png)

#### Step 5: Create New Branch and Use Rebase
In this step, you will create a new branch, make some changes on that branch, then rebase the new branch onto the main branch.

1. Create and switch to a new branch named **feature-branch**:
    ```
    git checkout -b feature-branch
    ```
- This command creates a new branch named **feature-branch** and switches you to that branch.

![Git](/Dung_aws/images/3.4/0007.png)

2. Create a new file **feature.txt** and add the content, then commit the changes:
    ```
    echo "This is a new feature" >> feature.txt
    ```
    ```
    git add feature.txt
    ```
    ```
    git commit -m "Add feature.txt with new feature description"
    ```

- **echo "This is a new feature" >> feature.txt**: Create a feature.txt file and add the line "This is a new feature".
- **git add feature.txt**: Add feature.txt file to staging area.
- **git commit -m "Add feature.txt with new feature description"**: Commit changes with message.

![Git](/Dung_aws/images/3.4/0008.png)

3. Switch to main branch (**main** or **master**):
    ```
    git checkout master
    ```

4. Create a new file **hotfix.txt**, add the content and commit the changes:
    ```
    echo "This is a hotfix" >> hotfix.txt
    ```
    ```
    git add hotfix.txt
    ```
    ```
    git commit -m "Add hotfix.txt with hotfix description"
    ```

![Git](/Dung_aws/images/3.4/0009.png)

5. Rebase the **feature-branch** to the **master branch**:
    ```
    git checkout feature-branch
    ```
    ```
    git rebase master
    ```

- Move **feature-branch** commits above **main** branch's latest commit.

![Git](/Dung_aws/images/3.4/0010.png)

#### Step 6: Using Cherry-pick
**Cherry-pick** in Git allows you to select one or more commits from another branch and apply them to the current branch. This is how you can bring in changes from a specific commit without having to merge the entire branch.

1. Create a new commit on the main branch (**main** or **master**):
- Switch to main branch (**main** or **master**):
    ```
    git checkout master
    ```

- Create a new file **anotherfix.txt**, add the content and commit the changes:
    ```
    echo "Another fix" >> anotherfix.txt
    ```
    ```
    git add anotherfix.txt
    ```
    ```
    git commit -m "Add anotherfix.txt with another fix"
    ```

![Git](/Dung_aws/images/3.4/0011.png)

2. **Cherry-pick** this commit into the **feature-branch**:
- Find the ID of the newly created commit. You can use one of the following commands to view commit history and get commit ID:
    ```
    git log --oneline
    ```
    ```
    git log --graph --oneline
    ```
- Switch to **feature-branch**:
    ```
    git checkout feature-branch
    ```
- Do a cherry-pick commit from the **main** branch to the **feature-branch** branch:
    ```
    git cherry-pick <ID_commit>
    ```
    Replace <ID_commit> with your actual commit ID.

![Git](/Dung_aws/images/3.4/0012.png)

#### Step 7: Using Stash
Stash in Git allows you to temporarily save uncommitted changes in the current work, so you can get back to working on something else without having to commit those changes immediately.

1. Make some changes on the **feature-branch**
- Suppose you are working on **feature-branch** and you make some temporary changes that are not ready to commit yet.
    ```
    echo "Some temporary changes" >> temp.txt
    ```

2. Check the status of Git
- Before **stash**, you can check Git's status to see which files have changed.
    ```
    git status
    ```
- You will see **temp.txt** as a changed file that has not been committed.

![Git](/Dung_aws/images/3.4/0013.png)

3. Add file to staging area
- You can add the changed file to the staging area:
    ```
    git add temp.txt
    ```

4. Stash changes
- Use the following command to stash uncommitted changes:
    ```
    git stash
    ```
    or use this command that provides you a message to describe the stash:
    ```
    git stash save "your message"
    ```
- **Note**, if the file are untracked or have not been added to the staging area, use the following command:
    ```
    git stash push --include-untracked
    ```
- When you run one of the above commands, Git will store your changes and restore the working directory status with no uncommitted changes.

![Git](/Dung_aws/images/3.4/0014.png)

5. Do some other work
- Now, you can do some other work. For example, switch to **main** branch and make some changes:
    ```
    git checkout master
    ```
    ```
    echo "Work on another task" >> another_task.txt
    ```
    ```
    git add another_task.txt
    ```
    ```
    git commit -m "Add another task"
    ```
![Git](/Dung_aws/images/3.4/0015.png)

6. Retrieve changes from stash
- Once you are done working on the other branch, you can go back to **feature-branch** and retrieve your stashed changes:
    ```
    git checkout feature-branch
    ```
    ```
    git stash apply
    ```

- The **git stash apply** command will retrieve the changes from the stash and apply them to the current branch.
- **Note**: If you want to delete the stash after it has been applied, you can use the command:
    ```
    git stash drop
    ```

7. Check the status again
- After applying the stash, you can check Git's status again to see that the changes have been rolled back.
    ```
    git status
    ```
![Git](/Dung_aws/images/3.4/0016.png)


<!-- #### Step 8: Using Submodules
Submodules allow you to embed another Git repository within an existing Git repository.

This is useful when you want to use another project as part of your project without copying the source code.

1. Create another project
- Create a new folder for the new project:
    ```
    mkdir NewProject
    ```
    ```
    cd NewProject
    ```
- Initialize repository:
    ```
    git init
    ```
- Create and add a file to the new project:
    ```
    echo "This is the new project" >> README.md
    ```
    ```
    git add README.md
    ```
    ```
    git commit -m "Initial commit for NewProject"
    ```
![Git](/Dungg_Git/images/3.4/0017.png)

2. Add Submodule to **GitProject**
- Move to **GitProject** project directory:
    ```
    cd <path/to/GitProject>
    ```
- Add new project as submodule from local directory:
    ```
    git submodule add <path/to/NewProject> submodules/NewProject
    ```
    + <path/to/NewProject>: This is the path to **NewProject**
    + **submodules/NewProject**: This is the path where the submodule will be stored in the GitProject folder

3. Commit changes in **GitProject**:
    ```
    git add .gitmodules submodules/NewProject
    ```
    ```
    git commit -m "Add NewProject as a submodule"
    ```

4. Check submodule:
    ```
    git submodule
    ``` -->






 