# Git Lawbook

## Get started

1. Download and setup **`SourceTree`**.
2. Download and setup **`Git`**.
	
	- Open console.
	- Try **`git status`** command.
	- If failed: download and install `git` to your PC.
3. Cloning project:

	- Open git of the project.
	- Press **`Code`** button.
	- Select **`HTTPS`** tab (the **`SSH`** way is more complicated and will cover later). 
	- Open console. 

	```
	cd desired/project/storage/path/
	git clone <HTTPS_LINK_COPIED_FROM_PROJECT_GIT>
	```

4. Open cloned project by SourceTree:
	
	- Select **`New...`** option.
	- Select **`Add Existing Local Repository`** option.
	- Select path to your project folder.

## Branch System

### 1. Creating a new branch
---------------------------

```
git checkout -b <BRANCH_NAME>
```

#### While naming your branch need follow next rules:
- **Use one of the prefixes:**

	**`feat/`** - to describe a branch for new feature (adding something)

	**`fix/`** - to describe a fix/hotfix for existing feature (fixing something)

	**`refactor/`** - to describe a code refactor (improving / optimisation)
	
	**`test/`** - to describe a test flow branch (**rare prefix**)
	
- **Use correct name styling:**

	After the prefix you need choose the name will describe the main purpose of branch. **For example: `feat/pin-screen-layout`, `fix/login-input-logic`, `refactor/user-saga`, `test/login-flow`**
	
	```
	NOTE! Use only lowercase letters. The splitter always is `-` (dash) symbol.
	Example: feat/some-very-long-branch-name
	```
	
### 2. Commit changes
---------------------------

Stage + commit all changes:

```
git add .
git commit -m "chore: some message here"
```

First of all, we are indexing all our files inside root directory (excluding .gitignore files). Then we commit changes locally (don't need an internet for this action).

#### While naming your message for commit need follow next rules:
- **Use one of the prefixes:**

	**`feat:`** - to describe a commit for new feature (adding something)
	
	**`fix:`** - to describe a fix/hotfix commit for existing feature (fixing something)
	
	**`refactor:`** - to describe a code refactor commit (improving / optimisation)
	
	**`test:`** - to describe new tests
	
	**`chore:`** - to describe some chore work (incrementing version / continuous integration / readme etc.)
	
- **Use `WIP` (work-in-progress) suffix if your changes aren't final.** 

- **Before commit check current branch (VSCode, SourceTree, console etc.).**

- **Use only `space` as word splitter.**

- **Do not duplicate an action. Wrong message examples: `feat: added ...` `fix: fixed ...` `refactor: refactored ...`**

```
NOTE! Commit your changes every 1-2 hours!
Its very important to staying up-to-date with your team.
```

### 3. Push commits to remote repository
---------------------------

### 3.1 Git: local credentials

Next commands allow us setup your credentials correctly for root directory git **(these creds will override your global git properties for current project)**:
 
```
git config user.name "Joe"
git config user.email "joe@gmail.com"
```

If you want add next config for all your projects, you can add `--global` flag:

```
git config --global user.name "Joe"
git config --global user.email "joe@gmail.com"
```

To list out all config you can write following:

```
git config -l
```

Press **`space`** to scroll down all of them).


### 3.2 Pushing commits


After one or few commits we can push our changes to remote storage:

```
git push origin feat/current-branch-example
```

You can check your project in **`SourceTree`**. There will be visible new commit in your branch (Do **`Fetch`** action there, if you can't see any new commits to update branches).

### 4. Branches movement
---------------------------

You can swap active branch any time you want:

```
git checkout feat/new-branch-example
```

or just use **`SourceTree`** for this purpose:

- Select desired branch from side-menu;

OR

- Select desired branch from branches-tree;

### 5. Pulling branches
---------------------------

```
NOTE! Check your active branch before.
```

You can pull changes from another branch with following commands:

```
git pull origin <DESIRED_BRANCH_NAME>
```

OR **`Pull`** button in **`SourceTree`** app -> Select desired branch.

### 6. Main & develop branches
---------------------------

Each git project starts with RELEASE branch called **`main`/`master`**.

```
NOTE! DON'T commit/push any changes forward there! This branch exists only for release versions and merges with help of Pull Requests!
```

For DEVELOPMENT versions/changes exists another branch that merges particular branches inside itself regularly (after Team Lead review)

This branch called **`develop`**

```
NOTE! DON'T work inside that branch! Create your OWN branch for current task!
```

If you see develop updates you can pull it to your active branch. **(Its useful)**

### 7. Pull Requests
---------------------------

After push all commits to your active branch of current task (task is done), you can open Pull Request to **`develop`** branch merged it previously.

- After pushes pull **`develop`** changes to your active branch:

```
git pull origin develop
```

(I recommend use **`Pull`** button from **`SourceTree`**)

- After success push action, go to the Git website, open your project and **`Pull Requests`** section.

- Select your branch as **SOURCE** and `develop` branch as **TARGET**

- Press `Open PR`

- Copy the link and paste it to your team channel for review