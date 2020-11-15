# giteasy

### Clone
```git
git clone https://github.com/ncoresoftopensource/giteasy
```

### Regist Account 
If you do a commit for the first time, you should check your information for the first time.   
`email` or `user-name`
```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
Typically, try entering the email corresponding to the first line.

### How to apply `gitignore` for the first time after setting it up
The gitignore file must exist at first.
```git
git rm -r --cached .
git add .
git commit -m "Apply .gitignore"
```
