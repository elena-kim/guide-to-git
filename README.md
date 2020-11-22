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
