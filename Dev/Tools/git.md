
## HOW TOs

### Updating and pushing from submodules

1. first `commit/push` your **_submodule's_** changes:

```bash
cd path/to/submodule
git add <stuff>
git commit -m "comment"
git push origin HEAD:main
```

2. Then, update your **_main project_** to track the updated version of the **_submodule_**:

```bash
cd /main/project
git add path/to/submodule
git commit -m "updated my submodule"
git push
```


## Common tasks

1. Git push tracking:  `git push -u <branch name>`
2. Git status untracked files (faster): `git status -uno`
3. Git show untracked diff: `git diff`
4. Git show staged diff: `git diff --cached`
5. Git stash changes: `git stash -m "<specific name>"`
6. Git stash list: `git stash list
7. Git pop stash top most changes: `git stash pop`

## Use different SSH Key

To use a specific ssh key for a git repository, add below to `~/.ssh/config`:

```
Host github.com-personal
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_github
```

and use this to clone the repository:

```shell
git clone git@github.com-personal:NayanJD/obsidian.git
```
