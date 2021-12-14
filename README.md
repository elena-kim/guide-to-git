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
- [Commit 수정](#commit-수정)
- [Config](#config)
- [Git Log](#git-log)
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

GitHub에서 소스를 최초로 내려받을 때 git clone 명령어를 사용합니다.  
Clone을 하기 위해서는 Git 저장소의 주소를 알아야 하는데, 주소 형식은 아래와 같습니다.

```
https://github.com/[USERNAME]/[REPOSITORY_NAME].git
```

<br>

예를 들어, 이 레포지토리를 Clone 하고 싶다면 아래와 같이 입력하면 됩니다.

```git
git clone https://github.com/devncore/the-easiest-git.git
```

<br />  

## Commit
Git의 Repository 구조는 **작업폴더(Working Direcory), 인덱스(Staging Area), 저장소(Head Repository)** 로 나눌 수 있습니다. 

![git](https://user-images.githubusercontent.com/74305823/145518503-56b2517d-8816-4dac-b2c1-65939d0be01b.png)

저장소에 Commit하기 위해서는 **`git add`** 명령어를 통해 추가 및 변경된 파일을 스테이징시켜야 합니다. <br>

```csharp
// 특정 파일만 Stage
git add [파일명]

// 변경사항 있는 모든 파일 Stage
git add .

// Stage된 파일 Unstage 
git rm --cached [파일명]
```

<br>

스테이징을 완료했다면 **`git commit -m [커밋 메시지]`** 명령어를 통해 저장소에 변경 내용을 적용합니다. <br>
이때 **`-m`** 앞에 **`-a`** 옵션을 추가하면 add와 commit을 한번에 할 수 있기 때문에 **`git add`** 를 생략할 수 있습니다.

```csharp
// -a 옵션 미적용
git commit -m "Fix Error"

// -a 옵션 적용
git commit -a -m "Fix Error"
```

<br>

## Commit 수정
Git은 로컬에 모든 버전관리 데이터를 복사해두고 있기 때문에 자유롭게 수정할 수 있습니다. 하지만 [Git 공식 문서](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)에도 쓰여 있듯, 이미 Push된 Commit에 대해서는 수정 작업을 지양해야 하며, 고쳐야 할 부분이 생겼다면 새로 수정작업을 추가하도록 합니다.

#### 1. 마지막 커밋 메시지 수정하기
**`git commit --amend`** 명령어를 통해 수정 가능하며, `-m "new message"`를 붙이면 텍스트 편집기 실행 없이 바로 커밋 메시지를 수정할 수 있습니다.

```csharp
// 텍스트 편집기 실행
git commit --amend

// 텍스트 편집기 실행X
git commit --amend -m "new message" 
```
  
<br>  

#### 2. 나중에 수정한 파일을 마지막 커밋에 밀어넣기
파일을 수정하고 **`git add`** 명령으로 Stage 시킨 후 **`git commit --amend`** 명령으로 커밋하면 커밋 자체가 수정되면서 추가로 수정사항을 밀어넣을 수 있습니다. 이때 SHA-1 값이 바뀌므로 과거의 커밋을 변경할 때 주의해야 합니다. <br>

만약 변경 내용이 많다면 커밋 메시지가 해당 내용을 담을 수 있도록 수정할 필요가 있습니다. 반면 변경 내용이 사소하거나 커밋 메시지가 충분히 반영하고 있다면 **`--no edit`** 옵션을 통해 커밋 메시지 수정을 건너뛸 수 있습니다.

```
git add new-file
git commit --amend --no-edit
```

<br>  

#### 3. Commit Author 수정하기
가장 최근 커밋이 아닌 예전 커밋을 수정하려면 **`rebase`** 명령을 이용해 수정할 수 있습니다. 어떤 시점부터 HEAD까지 Rebase할 것인지는 `HEAD~2`나 `HEAD~3` 등의 인자를 넘겨주면 됩니다. 예를 들어, 2번째 커밋의 Author를 바꾸고 싶다면 아래와 같이 입력합니다.

```
git rebase -i HEAD~2
```

<br>  

이때 rebase의 결과는 log 명령과 반대의 순서로 나타납니다. 즉, rebase 결과에서 제일 위에 있는 것이 더 오래된 커밋입니다.
|rebase|log|
|:--:|:---:|
|<img width="600" src="https://user-images.githubusercontent.com/74305823/145529917-f708132a-59f5-4d50-81de-1881f396a9e6.png">|<img width="669" src="https://user-images.githubusercontent.com/74305823/145530015-ca277f12-b19e-4f19-aa3c-e74b6a062153.png">|

<br>  

**`rebase`** 명령을 통해 vi화면이 뜨면 입력모드(i)로 진입 후, 변경할 커밋의 'pick'을 'e'로 바꿔주고 저장&종료(:wq)합니다. 그후에 아래 명령어로 변경할 Author 정보를 입력합니다.
```
git commit --amend --author="user.name <user.email>"
```
<img width="565" alt="스크린샷 2021-12-10 오후 3 41 50" src="https://user-images.githubusercontent.com/74305823/145530588-39ccbcff-df3d-4e19-9a23-fe04c9b5bdc4.png">

<br>  

이미 Push된 커밋이라면 `force`를 통해 수정된 커밋을 강제로 Push해줘야 합니다. 하지만 앞서 말했듯 이미 Push된 커밋을 수정하는 것은 지양해야 하며, 특히 `force pushing`은 Push된 커밋 로그를 갖고 있던 다른 팀원들이 로그를 수동으로 수정해줘야 하기 때문에 최대한 사용하지 않아야 합니다.

> _**We strongly discourage force pushing**, since this changes the history of your repository. If you force push, people who have already cloned your repository will have to manually fix their local history. For more information, see "Recovering from upstream rebase" in the Git manual._

<br>  

아래 명령을 통해 Remote에 변경사항을 적용할 수 있습니다.
```python
git rebase --continue
git push -f origin main   # git push -f [remote name] [branch name]
```
 
#### 4. Commit History 삭제하기
`reset` 명령어를 통해 지정한 Commit 이후의 모든 Commit History를 삭제할 수 있습니다. <br>
예를 들어, 아래 사진에서 노란색으로 표시된 커밋을 되돌아갈 시점으로 지정한다면 빨간색으로 표시된 3개의 커밋 기록이 삭제됩니다.

![reset](https://user-images.githubusercontent.com/74305823/137444338-a235fbd5-1ca3-479f-90f5-4e5ffe10aaae.png)

#### 명령어 
```
git reset {option} {되돌아갈 시점의 commit hash값}
```

#### 옵션
- hard: 파일을 포함한 모든 히스토리를 전부 삭제합니다. 
- soft: 히스토리만 삭제하고 파일은 stage 상태 그대로 남아 있습니다. 
- mixed: 디폴트 옵션으로, 히스토리를 삭제한 후 파일도 그대로 남아있지만 stage 상태는 아니기에 다시 add를 해야 추적이 가능합니다.

<br>
[3. Commit Author 수정하기](#3-commit-author-수정하기) 와 마찬가지로 이미 Push된 커밋은 아래 명령어를 통해 강제로 변경해줍니다.

```python
git push -f origin main  # git push -f [remote name] [branch name]
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
해당 레포지토리의 커밋 기록을 **`git log`** 명령어를 통해 확인할 수 있습니다.

```
git log
```

<img width="669" src="https://user-images.githubusercontent.com/74305823/145530015-ca277f12-b19e-4f19-aa3c-e74b6a062153.png">

가장 위에 있는 커밋이 최근 커밋이고 아래로 갈수록 오래된 커밋입니다. 커밋은 여러가지 정보들을 함께 저장하고 있는데 각 커밋의 SHA-1, Author 정보, 커밋 날짜, 커밋 메세지 등을 차례로 보여줍니다. 

### 옵션
- `-number` : number에 숫자를 입력하면 가장 최근 커밋에서 해당 개수만큼의 커밋 기록이 보입니다.
- `--pretty` : `--pretty=oneline`, `--pretty=format:"%H, %an` 등 원하는 포맷을 설정해 출력할 수 있습니다.
- `p`, `--patch` : 커밋들 간의 차이점을 볼 수 있습니다.
- `graph` : 브랜치를 그래프로 볼 수 있으며, `git log --oneline --decorate --graph --all` 명령어를 사용하면 main 브랜치에서 파생된 다른 브랜치도 확인할 수 있습니다. 

```
git log --date=short --pretty=format:%h,%an,%ae,%ad,%s > history.csv
```

<br/>
      
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

**Contributors 목록**
```
![](https://contrib.rocks/image?repo=devncore/leagueoflegends)
```

![](https://contrib.rocks/image?repo=devncore/leagueoflegends)

