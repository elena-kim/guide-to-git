
## Contents
- [Git Config](#config-)
- [Git Clone](#clone-)
- [Git Pull](#pull-)
- [Git Commit](#commit-)
- [Git Commit 수정](#commit-수정-)
- [Git Push](#push-)
- [Git Branch](#branch-)
- [Git Log](#log-)
- [Git 복구](#git-복구-)
- [Git Error](#git-error-)
- [Git HEAD](#git-head-)
- [Git Checkout](#git-checkout-)
- [Git Ignore](#git-ignore-)
- [GitHub Avatar](#github-avatar-)

<br />

## Config [🔝](#contents)
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

## Clone [🔝](#contents)

GitHub에서 소스를 최초로 내려받을 때 git clone 명령어를 사용합니다.  
Clone을 하기 위해서는 Git 저장소의 주소를 알아야 하는데, 주소 형식은 아래와 같습니다.

```
https://github.com/<USERNAME>/<REPOSITORY_NAME>.git
```

<br>

예를 들어, 이 레포지토리를 Clone 하고 싶다면 아래와 같이 입력하면 됩니다.

```git
git clone https://github.com/elena-kim/guide-to-git.git
```

<br/>

## Pull [🔝](#contents)
`git pull` 명령어는 원격 저장소의 정보를 가져오면서 자동으로 로컬 브랜치에 병합(Merge)까지 수행합니다.

```python
git pull origin master  # git pull <remote name> <branch name>
```

<br />

`git fetch` 명령어 또한 원격 저장소의 커밋 정보들을 로컬 저장소로 가져온다는 점에서 `git pull` 명령어와 비슷한 역할을 수행합니다. 하지만 자동으로 병합을 수행하지 않는다는 점에서 `git pull` 명령어와 차이가 있습니다.

<br />

## Commit [🔝](#contents)
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
(단, 한번도 add되지 않은 파일은 add를 따로 작업 해줘야함.)

```csharp
// -a 옵션 미적용
git commit -m "Fix Error"

// -a 옵션 적용
git commit -a -m "Fix Error"
```

<br>

## Commit 수정 [🔝](#contents)
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

## Push [🔝](#contents)
`git push` 명령어는 로컬 저장소에서 커밋 내용을 원격 저장소에 반영하기 위해 사용합니다.

```python
git push origin main  # git push <remote name> <branch name>
```

<br />

기본적으로 위와 같이 원격 저장소명과 브랜치명을 인수로 받지만, 매번 입력하는 일이 번거롭다면 아래와 같이 `-u` 옵션을 추가하면 됩니다. 이후에는 원격 저장소명과 브랜치명 없이 `git push` 명령어만 입력해도 해당 저장소에 push됩니다.

```python
git push -u origin main
```

<br />

## Log [🔝](#contents)
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

## Branch [🔝](#contents)

모든 버전 관리 시스템은 브랜치를 지원하는데, 개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생기게 됩니다. 이때 여러 개발자들이 원래 코드와는 상관없이 각자 독립적인 작업 영역 안에서 개발을 진행할 수 있게 해주는 기능이 바로 브랜치입니다. 

브랜치 종류에는 5가지가 존재하며 메인 Branch와 보조 Branch를 포함합니다.

| Master Branch | Develop Branch | Feature Branch | Release Branch | Hotfix Branch |
|:-------------:|:--------------:|:--------------:|:--------------:|:-------------:|
| 제품으로 출시될 수 있는 브랜치 | 다음 출시 버전을 개발하는 브랜치 |  기능을 개발하는 브랜치 (Local) | 이번 출시 버전을 준비하는 브랜치 | 출시 버전에서 발생한 버그를 수정하는 브랜치 |     

<br />

Branch와 관련된 주요 명령어는 아래와 같습니다.

<table>
  <thead>
    <th>역할</th>
    <th>명령어</th>
    <th>예시</th>
  </thead>  
  <tbody>
    <tr>
      <td align="center">  &nbsp;&nbsp;&nbsp; Branch 조회 &nbsp;&nbsp;&nbsp; </td>
      <td><code>git branch</code></td>
      <td><code>git branch</code></td>
    </tr>
    <tr>
      <td align="center">Branch 생성</td>
      <td><code>git branch [branch name]</code></td>
      <td><code>git branch lucas</code></td>
    </tr>
    <tr>
      <td align="center">Branch 전환</td>
      <td><code>git switch [branch name]</code></td>
      <td><code>git switch lucas</code></td>
    </tr>
    <tr>
      <td align="center">Branch 원격저장소</td>
      <td>
        <b>Branch List</b>
          <h6>1. 원격저장소 branch List 확인 </h6>
          <code>git branch -r [branch option]</code>
          <h6>2. 원격저장소와 로컬 모든 branch List 확인</h6>
          <code>git branch -a [branch option]</code>
        <br/><br/>
        <b> 원격저장소 Branch 가져오기 </b><br/><br/>
          <code>git checkout -t [remote명/branch명]</code>          
      </td>
      <td>
        <code>git branch -r</code><br/><br/>
        <code>git branch -a</code><br/><br/>
        <code>git checkout -t origin/lucas</code><br/><br/>
      </td>
    </tr>
    <tr>
      <td align="center">Branch 삭제</td>
      <td>
        <b>Local Repository</b>
          <h6>1. Merge 하지 않은 커밋이 없을 경우</h6>
          <code>git branch -d [branch name]</code>
          <h6>2. Merge 하지 않은 커밋이 있을 경우 (강제 삭제)</h6>
          <code>git branch -D [branch name]</code>
        <br/><br/>
        <b>Remote Repository</b><br/><br/>
        <code>git push origin --delete [branch name]</code>
      </td>
      <td>
        <code>git branch -d lucas</code><br/><br/>
        <code>git branch -D lucas</code><br/><br/>
        <code>git push origin --delete lucas</code>
      </td>
    </tr>
  </tbody>
</table>

<br/>

#### Branch Merge
#### 1. 로컬 브랜치(작업한 브랜치)를 다른 브랜치에 병합하기

로컬 브랜치에서 Commit을 진행한 후 병합할 브랜치로 변환합니다.

```python
# 현재 branch는 lucas
git add .
git commit -m "Update"
git switch main
```

`git merge` 명령어를 통해 main 브랜치로 병합을 진행합니다.
```python
git merge lucas   # git merge <commit한 branch> 
```

이후 충돌(Conflict)이 발생했다면 해당 부분을 수정하고, 없다면 `git push` 명령어로 커밋 내용을 적용합니다.
  
#### 2. 원격저장소의 브랜치를 다른 브랜치에 병합하기

로컬 브랜치를 원격저장소 브랜치에 Push한 후 PullRequest를 통해 병합이 가능합니다.

<br />

## Git 복구 [🔝](#contents)
`git rebase` 또는 `git reset` 등으로 커밋을 잘못 삭제했을 때 **`git reflog`** 명령을 통해 Git 이력을 확인하여 복구할 수 있습니다. <br>
`reflog`는 참조(reference)의 기록(log)을 보여주는 명령으로, 각 커밋의 이력과 Hash Id를 확인할 수 있습니다.

#### Commit 복구하기

```python
git reflog   
git reset --hard <hash id>
```

#### Branch 복구하기

```python
git reflog    
git checkout -b <삭제한 브랜치명> <hash id>
```

#### Stash 복구하기
아래 명령어를 통해 스태시 목록을 조회합니다.
```
git fsck --no-reflog | awk '/dangling commit/ {print $3}' | xargs -L 1 git --no-pager show -s --format="%ci %H" | sort
```
>❗dangling commit: 잃어버린 커밋이라는 뜻으로 어느 브랜치나 태그로부터도 참조되고 있지 않은 커밋 (stash도 포함)
<br>

복구하고자 하는 hash값을 확인한 후, 아래 명령어를 통해 해당 스태시를 복구합니다.
```
git stash apply {hash값}
```
<br/>

## Git Error [🔝](#contents)

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

## Git HEAD [🔝](#contents)
모든 브랜치에는 HEAD 값이 존재하며 HEAD는 해당 브랜치에 커밋 정보중 가장 마지막 커밋을 가리킵니다. <br />
지금 HEAD가 가리키는 커밋은 바로 다음 커밋의 부모가 되며 HEAD는 현재 브랜치를 가리키는 커밋에 대한 포인터입니다.

> 마지막 커밋 HEAD 정보  

<img src="https://user-images.githubusercontent.com/76234292/152634952-051e6929-fcee-4c14-be48-e3c5bfd74005.png" width="750"/>

<br/>

## Git Checkout [🔝](#contents)
Git 2.23 버전부터 `git checkout`의 기능이 `switch`와 `restore`로 분리되었습니다.

#### Switch
`git switch` 명령어를 통해 브랜치를 전환할 수 있습니다.

```python
git switch lucas # git switch <브랜치명>
```

#### Restore
`git restore` 명령어를 통해 수정한 파일 내용들을 되돌릴 수 있습니다. 

```python
git restore .           # 수정된 모든 파일 되돌리기
git restore README.md   # 특정 파일만 되돌리기
```

<br />

또한 `git add` 명령어를 통해 스테이지에 올라간 것을 다시 내릴 수도 있습니다.

 ```python
 git restore --staged test.txt  
 ```
 
<br/>

## Git Ignore [🔝](#contents)
Git 사이트 `gitignore` 문서에서 `gitignore` 파일은 "Git이 무시해야 하는 의도적으로 추적되지 않은 파일을 지정하며 Git에서 이미 추적한 파일은 영향을 받지 않습니다." 라고 설명하고 있습니다. <br />
실제로 프로젝트를 참여하고 개발을 진행하는 경우 불필요한 파일들이 많이 생성됩니다. 예를 들면 git pull 을 하는경우 작업자들의 작업환경이 모두 다르기 때문에 불필요한 파일을 다운받게 되는데 `.gitignore` 는 이러한 파일들을 git 관리 대상에서 제외하기 위해(commit에 포함하지 않도록) 규칙들을 저장한 파일입니다.

### .gitignore 파일 생성
아래의 사이트에서 원하는 프로젝트에 맞게 .gitignore 파일 생성
- https://www.toptal.com/developers/gitignore

### .gitignore 파일 적용
생성 및 작성한 .gitignore 파일을 git repository 최상위 디렉터리에 저장후 commit하여 원격 저장소에 push 합니다.

```python
git rm -r --cached .
git add. 
git commit -m "커밋메세지"
git push origin {브랜치명}
```

### .gitignore 작성규칙 예시

|||
|:-------------|:---------|
|특정 파일 제외하기|`readme.md`|
|현재 경로에 있는 파일만 제외하기|`/readme.md`|
|특정 폴더안의 파일 제외하기|`node_modules/`|
|특정 경로의 특정 파일 제외하기|`folder/file.txt`|
|특정 확장자 파일 제외하기|`*.txt`|
|예외 만들기|`!readme.md`|

<br />

## GitHub Avatar [🔝](#contents)
GitHub 사용자의 Avatar를 가져오는 방법에는 아래와 같은 것들이 있습니다.
```
https://avatars1.githubusercontent.com/devncore-james
https://github.com/devncore-james.png
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

