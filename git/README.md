# Git Hub

Git is a version control platform that helps you to organize, collaborate and share your scripts. 
You can open a free account for [github](https://github.com/)

After opening the accout, just follow up the instructions for setting up you GitHub account: 

- ## Set your git user name
  ```bash
    git config --global user.name "<your_name_here>"
  ```
- ## Set your git e-mail # if you have UF credentials, use them, we have access to **PRO accounts** 
  ```bash
  git config --global user.email "<your_email@email.com>"
  ```
 
After setting up your account, you can start using your git 
>Note: remember that you have your local git (your personal computer) and your remote git (your GitHub website).
So, if you make a change in your local git, you have to save it first with `git add .`, then commit (the change you want) the _change_ with 
`git commit -m 'Yes, I want to commit my last change'`, and finalize with pushing your local changes using `git push` to your _online git_


-	## Checking first 
	```bash
	git init
	git status
	```

-	## Clonning repository
	```bash
	git clone http://github.io/user_name/repository_name
	```
-	## Adding files 
	```bash
	git add .
	```
-	## Commiting files in-line commenting
	```bash
	git commit -m 'first commit of files'
	```

- ## Execute
	```bash
	git push
	git pull
	```
	if problems persist, force
	```bash
	git push -f
	```

# One commit ahead
-   ## Commit the change using
    
    ```bash
    git commit -m "My message"
    ```
      
-   ## Stash it.
    Stashing acts as a stack, where you can push changes, and you pop them in reverse order.
    
    To stash, type  
    ```bash
    git stash
    ```
    Do the merge, and then pull the stash:
    ```bash
    git stash pop
    ```
-	## Discard the local changes
	Using  
	```bash
	git reset --hard
	```
	or  
	```bash
	git checkout -t -f remote/branch
	```
- ## Discard large files, if commited large files mistakenly
To remove at commiting
```bash 
git filter-branch --tree-filter 'rm -rf PATH_TO_FILE' HEAD
```
OR
To remove after committing it first 
```bash 
git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch PATH_TO_FILE'
```
