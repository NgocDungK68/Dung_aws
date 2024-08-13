---
title : "Basic Commands"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3.3 </b> "
---

## Basic commands of Git

#### Set up personal authentication
    ```
    $ git config --global user.name "User Name"
    $ git config --global user.email "username@gmail.com"
    ```

#### Create a Git repository
    ```
    $ git init
    ```

#### Copy an existing repository
    ```
    $ git clone https://github.com/user/repository.git
    ```

#### **Branch** in Git
- Many different branches can be created. This command helps check the current branch.
    ```
    $ git branch
    ```

- Create a new branch
    ```
    $ git branch <name_branch>
    ```

- Switch and create a new branch
    ```
    $ git checkout -b <name_branch>
    ```

- Switch branch
    ```
    $ git checkout <name_branch>
    ```

#### Update changes
    ```
    $ git add .
    ```

- After adding, use **Commit** command to push all changes to **Local Repository**
    ```
    $ git commit -m "Message"
    ```

#### Update to server
- After **Commit**, the project is just updated to **Local Repository**. If you want to update to server, use **Push** command
    ```
    $ git push origin <name_branch>
    ```
- If not exist remote on server, you need to add a new remote before **push**
    ```
    $ git remote add origin <remote_url> 
    ```

    ```
    $ git push origin <name_branch>
    ```