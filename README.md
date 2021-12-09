<div align=center>
  <h2>The Easiest Git</h2>
  <br/>

  Git의 기본적인 사용법에 대해 기술한 레포지토리입니다.
  
  <br />

  이 레포지토리는 DevNcore팀이 관리하고 있습니다.
  
  <a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>

  <br />
 
  <p align="center">
   <a href="https://github.com/devncore/the-easiest-git/stargazers"><img src="https://img.shields.io/github/stars/devncore/the-easiest-git" alt="Github Stars"></a>
   <img src="https://img.shields.io/github/license/devncore/the-easiest-git" alt="License">
   <a href="https://github.com/devncore/the-easiest-git/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/the-easiest-git" alt="Commits-per-month"></a>
 </p>
</div>

<br />

## Contents
- [사용자 정보](#사용자-정보)
- [Clone](#clone)
- [Commit](#commit)
- [Config](#config)
- [Git Log](#git-log)
- [Log Graph](#log-graph)
- [Reset](#reset)
- [Switch Branch](#switch-branch)
- [Auto Login](#auto-login)
- [Git Avatar](#git-avatar)

<br />

## 사용자 정보 

Git 설치 후 가장 먼저 해야 하는 것은 사용자 이름과 이메일 주소를 설정하는 것입니다. <br>
본인의 모든 저장소에 동일한 Commit 정보를 적용하려면 아래 명령어를 차례로 입력하면 됩니다.

```git
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

<br>

만약 하나의 저장소에만 특정 사용자 정보를 저장하고 싶다면 `--global`을 `--local`로 변경하거나 생략합니다. <br>
`--local` 설정은 `--global`보다 우선적으로 적용됩니다.

```git
git config (--local) user.email "you@example.com"
git config (--local) user.name "Your Name"
```

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
- ### `Edit Last Commit`
```
git commit --amend
git commit --amend -m "new message" # direct
```
    
- ### `Last Commit Edit Save (Exit)`
```
`:wq` + `Enter`
```
    
- ### `Edit Commit Author`
예를 들어, 2번째 커밋의 Author를 바꾸고 싶다면 아래와 같이 입력합니다.
```
git rebase -i HEAD~2
```
![image](https://user-images.githubusercontent.com/74305823/135565874-99e8ae67-4ee5-4de7-a440-157c90ed7fb0.png)

vi화면이 뜨면 입력모드(i)로 진입 후, 변경할 커밋의 'pick'을 'e'로 바꿔주고 저장&종료(:wq)합니다.

![image](https://user-images.githubusercontent.com/74305823/135565972-ffd5c078-dd02-4dec-b84d-b2fca2a16a37.png)

아래 명령어로 Author 정보를 입력합니다.
```
git commit --amend --author="user.name <user.email>"
```
![image](https://user-images.githubusercontent.com/74305823/135566231-bf30fb9d-5b8f-4569-9e5c-b783afcfff84.png)

아래 명령어를 통해 Repository에 변경내용을 적용합니다.
```
git rebase --continue
git push -f origin main
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

<br />

## Reset
> 지정한 commit 이후의 모든 commit history가 삭제된다.  
<br>
예를 들어, 아래 사진에서 노란색으로 표시된 커밋을 되돌아갈 시점으로 지정한다면 빨간색으로 표시된 3개의 커밋 기록이 삭제된다.  

![reset](https://user-images.githubusercontent.com/74305823/137444338-a235fbd5-1ca3-479f-90f5-4e5ffe10aaae.png)

#### 명령어 
```
git reset {option} {되돌아갈 시점의 commit hash값}
git push -f {remote name}(origin) {branch name}
```

#### Option
- hard: 파일을 포함해서 모든 히스토리를 싹 날려버린다. 
- soft: 히스토리만 삭제하고 파일은 stage 상태 그대로 남겨둔다. 
- mixed: 디폴트 옵션으로, 히스토리를 삭제한 후 파일도 그대로 남아있지만 stage 상태는 아니기에 다시 add를 해야 추적이 가능하다.

## TBD
TBD.. 커밋 리스트 조회
```
git reflog
```

#### hash값 확인
해당 Repository의 Commit History에서 확인 가능하다.
![hash](https://user-images.githubusercontent.com/74305823/137443208-51f07446-000e-4ed3-873c-8a0cd5635bf4.png)

#### 예시
```
git reset --hard d35780b71a8725e39f45d3b84496a37102f6de07
git push -f origin main
```

<br/>
    
## Switch Branch
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
