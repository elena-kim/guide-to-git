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

### Git Log
```
git log
```

### Git Reset
```
git checkout . 한 다음에 다시 돌리는 방법: git reset (검증해봐야함)
```

### Git Auto Login
```
$ git config credential.helper store
$ git push http://example.com/repo.git (ex. git push https://github.com/ncoresoftsource/leagueoflegends.git)
Username: <type your username>
Password: <type your password>
```
Also we suggest to read [ gitcredentials](https://git-scm.com/docs/gitcredentials)
