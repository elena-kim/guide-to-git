# theeasiestgit.

### Clone
```git
git clone https://github.com/ncoresoftsource/theeasiestgit
```

### Regist Account 
If you do a commit for the first time, you should check your information. <br>
You can enter your `email` or `user-name` on the first line.
```git
git config --global user.email "you@example.com"
```
Or
```git
git config --global user.name "Your Name"
```
> If you want to use different account for each repository, just remove "--global" option.


### Change to Another Account 
다른 github 계정을 사용하고 싶을 때 cmd창에서 `Regist Account` 와 동일하게 입력
계정바꿔줬는데도 clone / push 등이 안되면 windows 자격증명에서 git 관련된 자격 증명 제거


### How to apply `gitignore` for the first time after setting it up
At first, the gitignore file exists unconditionally.
```git
git rm -r --cached .
git add .
git commit -m "Apply .gitignore"
```

### Last Commit Edit
```
git commit --amend
```
And direct
```
git commit --amend -m "new message"
```

### Last Commit Edit Save (Exit)
```
`:wq` + `Enter`
```

### Configure git
You can check your git configurations in cmd by entering below line.
```
git config --list
```

Your git configurations are saved in the `.gitconfig` file. And you can find this file in your home directory.
```git
[user]
	name = elena.kim
	email = elena.kim@ncoresoft.net
```

### Git Log
```
git log
```

### Git Reset
```
git checkout . 한 다음에 다시 돌리는 방법: git reset (검증해봐야함)
```

### Git Branch Switch
```
git checkout "branch name"
```

### Git Auto Login
```
$ git config credential.helper store
$ git push http://example.com/repo.git (ex. git push https://github.com/ncoresoftsource/leagueoflegends.git)
Username: <type your username>
Password: <type your password>
```
Also we suggest to read [ gitcredentials](https://git-scm.com/docs/gitcredentials)


### Git Log Graph
```git
git log --graph --oneline --all
```
