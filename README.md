# the-easiest-git

## Overview
- [Account](#account)
- [Clone](#clone)
- [Commit](#commit)
- [Config](#config)
- [Git Log](#git-log)
- [Log Graph](#log-graph)
- [Reset](#reset)
- [Branch Switch](#branch-switch)
- [Auto Login](#auto-login)
- [Git Avatar](#git-avatar)

## Account 
- ### `Regist`
If you do a commit for the first time, you should check your information. <br>
You can enter your `email` or `user-name` on the first line.
```git
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
:point_right: _If you want to use different account for each repository, just remove "--global" option._
<br />

- ### `Change`
It is same with [`Regist Account`](#regist)
```git
git config --global user.email "other@example.com"
git config --global user.name "Other Name"
```
다른 github 계정을 사용하고 싶을 때 cmd창에서 `Regist Account` 와 동일하게 입력
계정바꿔줬는데도 clone / push 등이 안되면 windows 자격증명에서 git 관련된 자격 증명 제거

<br />

## Clone
```git
git clone https://github.com/devncore/the-easiest-git
```
#### :point_right: _How to apply `gitignore` for the first time after setting it up?_
At first, the gitignore file exists unconditionally.
```git
git rm -r --cached .
git add .
git commit -m "Apply .gitignore"
```
<br />  

## Commit
- ### `Last Commit Edit`
```
git commit --amend
git commit --amend -m "new message" # direct
```
    
- ### `Last Commit Edit Save (Exit)`
```
`:wq` + `Enter`
```
<br />

## Config
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
<br/>
    
## Git Log
```
git log
```
<br/>
       
## Log Graph

```git
git log --graph --oneline --all
```
_TBD.._

## Reset
```
git checkout . 한 다음에 다시 돌리는 방법: git reset (검증해봐야함)
```
<br/>
    
## Branch Switch
```
git checkout "branch name"
```
<br/>
    
## Auto Login
```
$ git config credential.helper store
$ git push http://example.com/repo.git (ex. git push https://github.com/devncore/leagueoflegends.git)
Username: <type your username>
Password: <type your password>
```
Also we suggest to read [ gitcredentials](https://git-scm.com/docs/gitcredentials)

<br/>

## Git Avatar
```
https://avatars1.githubusercontent.com/devncore-james
```

**C# BitmapSource**
```csharp
string name = "devncore-elena";
var bitmapImage = new BitmapImage();
bitmapImage.BeginInit();
bitmapImage.UriSource = new Uri(string.Format("https://avatars1.githubusercontent.com/{0}", name);
bitmapImage.EndInit();
return bitmapImage;
```
