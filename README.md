##   The Easiest Git
이 리포지토리는 Git의 기본적인 사용법에 대해 기술한 리포지토리입니다. <br />
  
<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>

| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/the-easiest-git/stargazers"><img src="https://img.shields.io/github/stars/devncore/the-easiest-git" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/the-easiest-git" alt="License"> | <a href="https://github.com/devncore/the-easiest-git/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/the-easiest-git" alt="Commits-per-month"></a> |

<br />

## Contents
- [Config](#config)
- [Clone](#clone)
- [Commit](#commit)
- [Commit 수정](#commit-수정)
- [Git Log](#git-log)
- [Git Branch](#git-branch)
- [Git 복구](#git-복구)
- [Git Error](#git-error)
- [Git Avatar](#git-avatar)

<br />

## Config
**`git config`** 명령어를 통해 설정 내용을 확인하고 변경할 수 있습니다. Git 설정 파일은 아래 세 가지가 있습니다.

<table>
  <tbody>
    <tr>
      <td align="center"> <b>파일</b> </td>
      <td align="center"> <code>etc/gitconfig</code> </td>
      <td align="center"> <code>~/.gitconfig</code> <br> <code>~/.config/git/config</code> </td>
      <td align="center"> <code>.git/config</code> </td>
    </tr>
    <tr>
      <td align="center"> <b>옵션</b> </td>
      <td align="center"> <code>git config --system</code> </td>
      <td align="center"> <code>git config --global</code> </td>
      <td align="center"> <code>git config (--local)</code> </td>
    </tr>
    <tr>
      <td align="center"> <b>적용범위</b> </td>
      <td align="center"> 시스템의 모든 사용자 <br> 모든 저장소 </td>
      <td align="center"> 특정 사용자(현재 사용자) <br> 모든 저장소 </td>
      <td align="center"> 특정 사용자(현재 사용자) <br> 특정 저장소 </td>
    </tr>
    <tr>
      <td align="center"> <b>우선 적용순위</b> </td>
      <td align="center" colspan="3"> <b> local > global > system </b></td>
    </tr>
  </tbody>
</table>  

#### Config 설정하기

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

#### 설정 내용 확인하기
`git config --list` 명령을 통해 전체 Config 리스트를 확인할 수 있습니다. <br>
만약 특정 Key에 대한 설정 값을 확인하고 싶다면 `git config <key>` 명령을 사용하면 됩니다.

```csharp
// 전체 설정 내용 확인
git config --list

// 특정 설정 내용 확인
git config user.name
```

<br />

## Clone

GitHub에서 소스를 최초로 내려받을 때 git clone 명령어를 사용합니다.  
Clone을 하기 위해서는 Git 저장소의 주소를 알아야 하는데, 주소 형식은 아래와 같습니다.

```
https://github.com/<USERNAME>/<REPOSITORY_NAME>.git
```

<br>

예를 들어, 이 레포지토리를 Clone 하고 싶다면 아래와 같이 입력하면 됩니다.

```git
git clone https://github.com/devncore/the-easiest-git.git
```

<br/>

## Commit
Git의 Repository 구조는 **작업폴더(Working Direcory), 인덱스(Staging Area), 저장소(Head Repository)** 로 나눌 수 있습니다. 

![git](https://user-images.githubusercontent.com/74305823/145518503-56b2517d-8816-4dac-b2c1-65939d0be01b.png)

저장소에 Commit하기 위해서는 **`git add`** 명령어를 통해 추가 및 변경된 파일을 스테이징시켜야 합니다. <br>

```csharp
// 특정 파일만 Stage
git add <파일명>

// 변경사항 있는 모든 파일 Stage
git add .

// Stage된 파일 Unstage 
git rm --cached <파일명>
```

<br>

스테이징을 완료했다면 **`git commit -m <커밋 메시지>`** 명령어를 통해 저장소에 변경 내용을 적용합니다. <br>
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
git add <파일명>
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

> _**We strongly discourage force pushing**, since this changes the history of your repository. If you force push, people who have already cloned your repository will have to manually fix their local history._

<br>  

아래 명령을 통해 Remote에 변경사항을 적용할 수 있습니다.
```python
git rebase --continue
git push -f origin main   # git push -f <remote name> <branch name>
```
 
<br> 
 
#### 4. Commit History 삭제하기
**`reset`** 명령어를 통해 지정한 Commit 이후의 모든 Commit History를 삭제할 수 있습니다. <br>
예를 들어, 아래 사진에서 노란색으로 표시된 커밋을 되돌아갈 시점으로 지정한다면 빨간색으로 표시된 3개의 커밋 기록이 삭제됩니다.

![reset](https://user-images.githubusercontent.com/74305823/137444338-a235fbd5-1ca3-479f-90f5-4e5ffe10aaae.png)

<br>

```python
# git reset <option> <되돌아갈 시점의 commit hash값>
git reset --hard d35780b71a8725e39f45d3b84496a37102f6de07  
```

#### 옵션
- `hard` : 파일을 포함한 모든 히스토리를 전부 삭제합니다. 
- `soft` : 히스토리만 삭제하고 파일은 Stage 상태 그대로 남아 있습니다. 
- `mixed` : 디폴트 옵션으로, 히스토리를 삭제한 후 파일은 남아있지만 Stage 상태는 아니기에 다시 add를 해야 추적이 가능합니다.

<div align="center">
  <img src="https://user-images.githubusercontent.com/74305823/146884108-39c45e31-018f-42c9-90ae-e7d8d6349402.png" width="700"/>
</div>
  
<br>

[**Commit Author 수정하기**](#3-commit-author-수정하기)와 마찬가지로 이미 Push된 커밋은 아래 명령어를 통해 강제로 변경할 수 있습니다.

```python
git push -f origin main  # git push -f <remote name> <branch name>
```

<br />

## Git Log
해당 레포지토리의 커밋 기록을 **`git log`** 명령어를 통해 확인할 수 있습니다.

```
git log
```

<img width="669" src="https://user-images.githubusercontent.com/74305823/145530015-ca277f12-b19e-4f19-aa3c-e74b6a062153.png">

가장 위에 있는 커밋이 최근 커밋이고 아래로 갈수록 오래된 커밋입니다. 각 커밋의 SHA-1, Author 정보, 커밋 날짜, 커밋 메세지 등을 확인할 수 있습니다. 

#### 옵션
- `-number` : number에 숫자를 입력하면 가장 최근 커밋에서 해당 개수만큼의 커밋 기록이 보입니다.
- `--pretty` : `--pretty=oneline`, `--pretty=format:"%H, %an` 등 원하는 포맷을 설정해 출력할 수 있습니다.
- `p`, `--patch` : 커밋들 간의 차이점을 볼 수 있습니다.
- `graph` : 브랜치를 그래프로 볼 수 있으며, `git log --oneline --decorate --graph --all` 명령어를 사용하면 main 브랜치에서 파생된 다른 브랜치도 확인할 수 있습니다. 

```
git log --date=short --pretty=format:%h,%an,%ae,%ad,%s > history.csv
```

<br/>

## Git Branch

모든 버전 관리 시스템은 브랜치를 지원하는데, 개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생기게 됩니다. 이때 여러 개발자들이 원래 코드와는 상관없이 각자 독립적인 작업 영역 안에서 개발을 진행할 수 있게 해주는 기능이 바로 브랜치입니다. 

브랜치 종류에는 5가지가 존재하며 메인 Branch와 보조 Branch를 포함합니다.

| Master Branch | Develop Branch | Feature Branch | Release Branch | Hotfix Branch |
|:-------------:|:--------------:|:--------------:|:--------------:|:-------------:|
| 제품으로 출시될 수 있는 브랜치 | 다음 출시 버전을 개발하는 브랜치 |  기능을 개발하는 브랜치 (Local) | 이번 출시 버전을 준비하는 브랜치 | 출시 버전에서 발생한 버그를 수정하는 브랜치 |     

#### Branch 조회

```
git branch
```

#### Branch 생성

```python
git branch lucas   # git branch <브랜치명>
```

#### Branch 전환

```python
git checkout lucas   # git checkout <브랜치명>
```

#### Branch 병합 

```python
git checkout main
git merge lucas     # git merge <병합할 브랜치명>
```

#### Branch 삭제   

> ##### Local Repository

```python
git branch -d lucas   # git branch -d <브랜치명>
```

아직 Merge 하지 않은 커밋이 있을 경우 위의 명령으로 삭제되지 않기 때문에 병합 상태와 관계없이 강제로 삭제하려면 `-D` 옵션을 사용합니다.

```python
git branch -D lucas   # git branch -D <브랜치명>
```

<br />

> #### Remote Repository
아래 명령어를 통해 원격저장소에 올라가 있는 브랜치를 삭제할 수 있습니다.

```
git push origin --delete lucas   # git push origin --delete <브랜치명>
```

<br />
      
## Git 복구
`git rebase` 또는 `git reset` 등으로 커밋을 잘못 삭제했을 때 **`git reflog`** 명령을 통해 Git 이력을 확인하여 복구할 수 있습니다. <br>
`reflog`는 참조(reference)의 기록(log)을 보여주는 명령으로, 각 커밋의 이력과 Hash Id를 확인할 수 있습니다.

#### commit 복구하기

```python
git reflog   
git reset --hard <hash id>
```

#### Branch 복구하기

```python
git reflog    
git checkout -b <삭제한 브랜치명> <hash id>
```
<br/>

## Git Error

#### 1. Git Push Error
```
fatal: The current branch lucas has no upstream branch.  
To push the current branch and set the remote as upstream, use
git push --set-upstream origin lucas
```
Git Push 명령어를 실행할 때 위와 같은 에러 메시지가 출력되면 원격저장소 이름을 확인한 후 원격저장소명을 명시해 Push 합니다.

```python
git remote -v
git push origin lucas   # git push <remote name> <branch name>
```
<br />

#### 2. SSL 403 Error
Git Clone 과정에서 SSL 403 에러가 생길 경우 아래 `http.sslverify` 옵션을 변경합니다.
```
git config --global http.sslVerify false
```

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

<br />
