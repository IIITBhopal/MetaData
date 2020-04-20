# Get familiar with Git

This document aims at providing enough git information to make your contributions
to any open source software a lot smoother.
This tutorial aims at the most useful commands which you are going to use in your
day to day github interactions.
It's my personal list of commands which I regularly use and believe my I seldom
need to use any other commands.

### Introduction

There are plenty of version control systems which help and ease the life
of a programmer empowering her/him/them to make mistakes, try something new
and browse back and forth the software development process.

#### So what is a version control system ??

A version control system as the name suggests tracks and controls the
versioning of a system often by recording the state of a system at a given 
moment in time.

#### Which VCS should I use ??

Git (mic drop).

### How to git ??

There are a lot of things you can do with git but not all of the features
will prove much useful in your day to day programming life.
For full guide on how to use git visit git's [official documentation](https://git-scm.com/docs).
And for now, you just need to learn, to properly use, these commands :-

* **git __clone__**.
* **git __branch__**.
* **git __checkout__**.
* **git __pull__**.
* **git __diff__**.
* **git __add__**.
* **git __commit__**.
* **git __log__**.
* **git __remote add__**.
* **git __config__**.
* **git __push__**.
* **git __rebase__**.

Let's go through them one by one.

* **git __clone__** :-	Clones the specified repository from a remote source into your
			local machine. You will need this command once for a project.

	1. *Usage* :

				`git clone <git-repository-url>`

			For e.g., to clone *this* repository you have to 

				`git clone https://github.com/IIITBhopal/MetaData`

* **git __branch__** :-	This and all other commands have plenty of options that go
			with them for many purposes. I will list the ways I find it useful.
	
	1. *Usage* : 	This command shows you all the branches of the current repository
			in your local system.

				`git branch`

	2. *Usage* :	To list all the branches in the local and remote repository.

				`git branch -a`

	3. *Usage* : 	To delete a branch.

				`git branch -d <merged-branch-name>`

				`git branch -D <any-branch-you-want-to-delete>`

* **git __checkout__**:	This and all other commands have plenty of options that go
			with them for many purposes. I will list the ways I find it useful.

	1. *Usage* :- 	Browse through the branches.

				`git checkout master // Take me to the master branch`

				`git checkout first-patch // Take me to the first-patch branch`

	2. *Usage* :- 	Create a new branch and switch to it.

				`git checkout -b enhancement#5`

* **git __pull__**:	Update the local repository to the remote repository.

	1. *Usage* :
				`git pull <remote-repo-url> <branch-name>`
			
			Check the branch you are in currently before issuing this command.
			Because the command `git pull` will apply the changes to the current branch.
			And in most of the case you certainly want the changes to be applied to the
			master branch.

			Thus, do this :- 
				
				`git checkout master`

				`git pull <remote-repo-url> master`

	2. *Usage* :	To set a local tracking branch which will track a remote branch.
			This situation often comes.

			Thus, do this :-

				`git checkout -b <branch-name>`

				`git pull <remote-repo-url> <branch-name> //Use same branch name.`

	3. *Info* :-	This command unlike others is a composition of two commands.

				`git fetch` and `git merge`.

			What it does is, it fetches the remote branch or repository and 
			merges it with your current branch.
			That is,

				`git pull <remote-repo-url> <branch-name>`

			can also be issued as

				`git fetch <remote-repo-url> <branch-name> //This downloads all the changes.`

				`git merge // This applies those changes to the current branch`

* **git __diff__** :-	Once you make your changes and save them to the disk, you can view it with this command.

	1. *Usage* :- 	Just do	

				`git diff` // Will display the changes you have made in a text format.

	2. *Usage* :- 	If you want to see changes between two branches or two commits, do this

				`git diff master...<branch-name> //Changes in <branch-name> against master.`
						or
				`git diff <branch-name_1>...<branch-name_2> //Changes in second branch against the first.`
						or
				`git diff <commit-hash_1>...<commit-hash_2> //Changes in second commit against the first.`
						or
				`git diff HEAD~3...HEAD //Current changes against the third last commit.`

	3. *Usage* :-

				`git diff --cached //Shows staged changes.`

* **git __add__** :-	Once you have made the changes and are content with them, "stage" them.
			This command adds the changes you have made to the index, a necessary step before
			commiting your changes.

	1. *Usage* :- 	Stage all the changes you have made in all the files.

				`git add .`

	2. *Usage* :-	Stage changes you have made in particular files.

				`git add <file-name> ... //List the files you have changed to add to the index.`

* **git __commit__**:-	Once you have made the changes and staged them, it's time for you to commit them.

	1. *Usage* :- 	Commit the changes.
			This command will prompt you to specify the commits' name and give a short description.

				`git commit`

	2. *Usage* :-	Same as the above but let's you commit the changes directly without staging them.
			Equivalent to :-
			1. `git add .`
			2. `git commit`

				`git commit -a`

	3. *Usage* :-	Same as git commit but it doesn't prompt you for description.

				`git commit -m <short-description>`

	4. *Usage* :-	Let's you sign the commit with your private key.

				`git commit -S`
			

	5. *Usage* :-	Does all of the above.

				`git commit -a -S -m <short-description>`

* **git __log__** :-	This command lets you browse the history of the current branch in the repository.
			This will show all the commits and their hashes, author,commit messages, description
			and date. Just issue the command

				`git log`

			and you can see the history.
			By default, shows the recent changes first.
			It shows the history of the local repository and the branch you are currently in.

* **git __push__** :-	Once you have made your changes and commited them in your local repository, it's time for
			you to push these changes to the remote repository.

	1. *Usage* :-	Push the changes, if the remote repository doesn't have the branch you created for this 
			specific task do this,

				`git push <remote-repo-url> +<branch-name> //note the '+' symbol there.`

	2. *Usage* :-	If the remote repository already has the branch remove the '+' symbol from the above command

				`git push <remote-repo-url> <branch-name>`

	3. *Usage* :-	If you have changed the git history through the rebase command, you will need to force push
			the current branch with the --force flag.

				`git push --force <remote-repo-url> <branch-name>`

			All of the above command will prompt you for your github username and password.
			Remember, you can make changes only to the repositories you have write access to.
			Thus you will find yourself making pushes against your own forked repositories, explained later
			in github workflow section.

* **git __remote__**:	If you are tired of typing the full repository URL then probably you want to add some form
			of variables to hold their value.
			This can be done with the git command,

				`git remote add`

	1. *Usage* :-

				`git remote add <unique-name> <remote-repo-url>`

			For example, for this repository you would want to add remote variable which look
			something like this,

				`git remote add origin https://github.com/IIITBhopal/MetaData`

				`git remote add upstream <Your-Forked-Repository-URL>`

			The remote variable origin is automatically added when you clone the repository.
			You need to add a variable which points to your forked repository for the push commands.
			That is, you will pull like this,

				`git pull origin master`

			and push like this,

				`git push upstream <branch-name>`

* **git __config__** :-	Configure your profile for the repository or globally on your local machine.

	1. *Usage* :- 	Add your bio information

				`git config user <Your-Name-or-Github-Username>`

				`git config email <Your-Github-Email-ID>`

	2. *Usage* :- 	If you do not want to set the above information again and again for every repository
			you should make them global by

				`git config --global user <Your-Name-or-Github-Username>`

				`git config --global email <Your-Github-Email-ID>`

	3. *Usage* :-	If you want to see the config information for your current repository, then browse to the root
			of the tree and do

				`cat .git/config`

			This displays the config file under .git directory which contains all the configuration information.

* **git __rebase__** :-	If you want to clear your local branch's git history, which you will surely want to do,
			you will frequently need this command after making commits or before pushing them.
			The command actually rewrites, rewords, rearranges and squashes the commits.

	1. *Usage* :-	Squashing last N number of commits.

				`git rebase -i HEAD~N`

			The above command will display the last N commits with their hash information preceded by the 
			keyword 'pick'.
			You can change the ordering of the commits and/or the keyword pick to suite your requirements.

	2. *Usage* :-	Rebasing your branch to another branch/master branch.
			After doing something like this :-

				`git checkout master`

				`git pull origin master`

			i.e. updating your master branch with the remote master branch, you can rebase your current branch
			on top of the new changes introduced in the master branch by

				`git checkout <branch-name>`

				`git rebase master`

			This can be done on any branch and against any branch.

	3. *Note* :-
			- Please note that rebasing only succeeds when their are no merge conflicts in your commits.
			
		  	- The command 'git pull' can introduce a merge commit in your git history, which is usually not the
			behaviour you want normally.
			For this you can do the following :-

			`git fetch origin <branch-name>`
					or
			`git fetch upstream <branch-name>`
					and
			`git rebase`


Thanks for reading such a long text. But, now you have enough information to start contributing to any Open Source community.
