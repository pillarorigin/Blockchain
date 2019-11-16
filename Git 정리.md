### 작업 흐름 요약 

```
1 단계
	git 설치 
	로컬 저장소로 만들 폴더 안에서 git bash
	(로컬저장소는 git이 관리하는 3개의 줄기로 구성)
		1. 디렉토리는 실제 파일들로 이루어져 있고
		2. 인덱스는 준비영역의 역할을 하며
		3. 헤드는 최종 확정본(commit) 을 나타냅니다.

	
2 단계
	git 구성 (config)
	$ git config --global user.name "USERNAME"
	$ git config --gliobal user.email "USEREEMAIL@mail.com"
	
	
3 단계 
	github사이트에서 원격저장소(repository) 생성
	README.md 작성
	git remote add origin <remote repository URL>
	git 초기화 ($ git init)
	
	
4 단계
	"Edit/Stage/Commit/Push" cycle.
	$ git status
	$ git add . (`add` 명령어는 인덱스(두번째 줄기)에 추가하는 것)
	
5 단계 
	.gitignore 설정

6 단계
	commit 후 push
	$ git status
	$ git commit -m "commit message" (`commit`명령어는 헤드에 추가해서 실제로 변경 내용을 확정.)
	$ git push origin master (`push`명령어는 Git의 원격 저장소에 반영을 합니다.)

7 단계
	태그 지정
	$ git tag -a v1.1 -m "버전 1.1"
	// -a 주석이 달린 태그를 생성하려면 -m 메시지를 제공하려면 -m 
	$ git push origin --tags
```

OR

```
$ git add -A //or, git add --all

$ git commit -m "commit messgae"

$ git push
```





### 1. Git의 개발 배경

Git은 리눅스 커널 개발을 지원하기 위해 2005 년 Linus Torvalds에 의해 설계되고 개발

### 2. Git의 구성

GIT는 VCS (Version Control System). (VCS는 모든 히스토리 개정을 포함하여 프로그램 코드 의 저장소 (또는 저장소 ) 역할 

- RCS (Revision Control System) 
- SCM (Source Code Manager)

### 3. Git 설치

- ubuntu

```
$ sudo apt-get install git
```

- windows or mac

```
http://git-scm.com/downloads 에서 다운로드 한 설치 프로그램 실행
```

### 4. Git Customize

```
// 커밋에 사용되는 사용자 이름과 이메일을 설정합니다. 
```

- ubuntu

```
$ git config --global user.name " your-name " 
$ git config --global user.email " your-email@youremail.com "
```

- windows

```
(git 설치한 디렉토리에서) $ git bash 실행 후
$ git config --global user.name " your-name " 
$ git config --global user.email " your-email@youremail.com "
```

### 5. Git 설정

The settings are kept in "<GIT_HOME>/etc/gitconfig" (of the GIT installed directory) and "<USER_HOME>/.gitconfig" (of the user's home directory.

You can issue "git config --list" to list the settings:

```
$ git config --list
user.email=xxxxxx@xxxxxx.com
user.name=xxxxxx
```

### 6. Git 기본 (index - commit - push)

```
$ git <명령(command)><인자(arguments)>
```

일반적으로 사용하는 명령은 다음과 같습니다.

1. init, clone, config: Git 프로젝트 시작
2. add, mv, rm: 파일 변경 준비
3. commit, rebase, reset, tag:
4. status, log, diff, grep, show: 상태 표시
5. checkout, branch, merge, push, fetch, pull
6. git help or git -- help : 도움말 [git mother site]: https://git-scm.com/docs

### 7. Git Storage Model

[사진 첨부 # Git_StorageDataFlow.png]

![image](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_StorageDataFlow.png)

### 8. Git 로컬 repo 시작

git 프로젝트 시작 방법은 2가지가 존재합니다. 

1. **자신의 프로젝트 새로 시작**  하는 방법

2. **Git host에서 기존 프로젝트 복제(clone)**하는 방법

   

1. **자신의 프로젝트 새로 시작**

   1). 새로 시작 시 디렉토리 설정. 자신의 프로젝트를 설명하기 위한 "README.md"파일 을 작성하는게 좋습니다.

    (Markdown구문의 텍스트 파일을 제공하는 것이 더 좋습니다) 

   [MarkDown]: https://help.github.com/en/github/writing-on-github

   2). 새로운 git repo를 초기화 (해당 프로젝트 디렉토리로 들어가서 초기화해야 합니다.

   ```
   $ cd / 해당하는 프로젝트 경로/
   $ git init
   ```

   git init 명령어를 입력한 뒤에 해당하는 local repo는 비어있어야 합니다. 파일을 명시적으로 repo에 deposit해주어야 합니다. (Before we proceed, it is important to stress that Git manages changes to files between so-called commits. In other words, it is a version control system that allows you to keep track of the file changes at the commits.

   3). Staging File 변경 사항 추적

   ```
   $ git status
   ```

   4). 파일 추가 (git add ...)

   ```
   $ git add .
   //현재 디렉토리의 모든 것을 추가 하겠습니다.
   
   $ git add <해당 파일.확장자명>
   //와일드 카드 패턴이 있는 하나 이상의 파일 이름 또는 경로 사용
   ```

   5). 파일 변경 커밋 (git commit -m "커밋 메세지")

   ```
   $ git commit -m "file name"
   
   // commit한 log 보기
   $ git log --[옵션 --oneline --file-pattern --author ="<author-name-pattern"]
   
   // 각 커밋은 40 자리 16 진수 SHA-1 해시 코드로 식별. 
   // 커밋을 참조하기 위해 처음 7 개의 16 진수를 사용
   ```

   6). 

   

2. **Git host에서 기존 프로젝트 복제(clone)**하는 방법

   1)  복제

   ```
   $ git clone <remote-url> 
   ```

   2) 

### 9.  원격 저장소 설정(Setting up Remote Repo)

1.  저장소 종류:

   - Github  (  public  프로젝트의 경우 무제한;  private  프로젝트의 경우 요금 )

   - BitBucket  ( public  프로젝트의 경우 무제한 사용자, private  프로젝트의 경우 5 명의 무료 사용자, 학업 계획의 경우 무제한 )

2. 로컬 스토리지 설정( `git remote add  `. )

   관습에 따라 원격 저장소의 이름을 " origin"로 지정

   ```
   // 로컬 리포지토리의 작업 디렉토리로 디렉토리 변경 
   $ cd / path-to / hello-git 
   // "git remote add <remote-name> <remote-url>"을 통해 "origin"이라는 원격 리포지토리 추가 
   // 예제의 경우 , 
   $ git remote add origin https://github.com/ your-username /test.git               // for GitHub 
   $ git remote add origin https : // username @ bitbucket.org / your-username /test.git   // for 비트 버킷
   ```

   // URL은 HTTPS 또는 SSH 형식 가능.

3. local storage에 push

   ```
   $ git push -u <remote-name> <local-branch-name>
   // 브랜치 "master"의 모든 커밋을 원격 저장소 "origin"으로 푸시합니다. 
   $ git push origin master 
   ```

   

### 10. `.gitignore` 파일

```
# 주석
* .class # 실행 파일 
* .exe # 객체 및 아카이브 파일 # [oa]는 o 또는 
*. [oa] 와 일치하는 정규 표현식을 사용할 수 있습니다 . 
# temp 하위 디렉토리 ( 디렉토리 구분자) 
temp /
```



###  11. Branch / merge

1. Git 데이터 구조

   - 모든 커밋과 파일 내용을 저장 하는 불변의 추가 전용 *객체 데이터베이스* (또는 *로컬 저장소* );

   - 준비된 정보를 캐시 하는 가변 *스테이징 영역* (또는 *인덱스* 또는 *캐시* )

     ![영상](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_Objects.png)

     The object database contains these objects:

     - Each version of a file is represented by a *blob* (binary large object - a file that can contain any data: binaries or characters). A blob holds the file data only, without any metadata - not even the filename.
     - A *snapshot* of the working tree is represented by a *tree* object, which links the blobs and sub-trees for sub-directories.
     - A *commit* object points to a tree object, i.e., the snapshot of the working tree at the point the commit was created. It holds metadata such as timestamp, log message, author's and committer's username and email. It also references its parent commit(s), except the root commit which has no parent. A normal commit has one parent; a merge commit could have multiple parents. A commit, where new branch is created, has more than one children. By referencing through the chain of parent commit(s), you can discover the history of the project.

     Each object is identified (or named) by a 160-bit (or 40 hex-digit) SHA-1 hash value of its contents (i.e., a content-addressable name). Any tiny change to the contents produces a different hash value, resulted in a different object. Typically, we use the first 7 hex-digit prefix to refer to an object, as long as there is no ambiguity.

     There are two ways to refer to a particular commit: via a branch or a tag.

     - A branch is a mobile reference of commit. It moves forward whenever commit is made on that branch.
     - A tag (like a label) marks a particular commit. Tag is often used for marking the releases.

2. Branch

   - Git의 브랜치는 커밋 중 하나에 대한 경량의 이동 가능한 포인터입니다.

   -  Git은 또한 `HEAD`현재 작업중인 브랜치를 추적하기 위해 호출되는 특수 포인터를 사용합니다.

     

   -  1) git 프로젝트를 만들어서 확인해봅시다.

     ```
     $ git init 
     $ git add README.md 
     $ git commit -m "Commit 1" 
     
     // README.md에 줄 추가 :이 줄은 커밋 1 뒤에 추가됩니다 
     $ git status 
     $ git add README.md 
     $ git commit -m " 커밋 2 " 
     
     // README.md에 줄 추가 :이 줄은 커밋 2 후에 추가됩니다 
     $ git status 
     $ git add README.md 
     $ git commit -m"Commit 3 " 
     ```

     ![이모](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_Branch1.png)

     

   - 2) 새로운 브랜치 만들기

     (**git branch <branch-name>**)

     ![이모](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_Branch2.png)

     새 분기를 만들 때 HEAD 포인터가 여전히 현재 분기를 가리킴.

     

   - 3) Switching to a Branch

     ##### (git check out <branch-name>)

     ![imgae](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_Branch3.png)

     HEAD가 분기로 전환.

     

   - 4) master로 HEAD포인터 이동

   -  5) `master`브랜치 에서 계속 작업 하고 커밋하면 `HEAD`포인터가 `master`브랜치에서 앞으로 이동합니다 . 두 가지가 이제 *분기* 됩니다. 

     ![이모](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_Branch6.png)

      `devel`분기 를 체크 아웃하면 파일 내용이 Commit-4로 되돌아감.

     ```
     $ git checkout devel
     ```

     

3. Merge

   #### ( git merge <branch-name> )

   1) **Fast-Forward Linear Merge**

   -  merge 할 분기가 직접 하위 항목 인 경우 Git은 포인터 `HEAD`를  앞으로 이동하여 Fast-Forward Linear Merge 를 합니다. 

   - 예를 들어, 현재 `devel`commit -4 브랜치에서 작업을 하고 있고 `master`브랜치의 최신 커밋이 commit-3에 있다고 가정합니다 . 

     ![이모](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_MergeForward.png)

     새로운 commit이 생성되지 않습니다.

     

   2) **3-Way Merge**

   -  두 분기가 분기되면 git은 자동으로 *공통 상위 커밋을* 검색 하고 3-Way Merge을 수행합니다. 충돌이 없으면 새로운 커밋이 생성 

     ![이모](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_Merge3Way.png)

   - git이 충돌을 감지하면. 병합을 일시 중지. 충돌을 해결하도록 사용자에게 요청을 함. 충돌이 해결되면 다시 `git add <file>`을 통해 파일을 준비.

   - 프로세스 상 새로운 commit이 생성됩니다.

     

   3) 병합 된 분기 삭제

   ##### ( git branch -d <branch-name> )

   merge가 된 예)devel은 더 이상 필요하지 않으므로 삭제할 수 있다.

   ```
   $ git branch -d devel 
   삭제 된 브랜치 디벨 (기존 a20f002). // 최신 커밋 
   $ git branch devel //에서 개발 브랜치를 다시 만듭니다.
   ```

   

4. Rebase branch

    리베이스 작업의 기본 목적은 선형 프로젝트 이력을 유지하는 것 

   

### 12. Branch / merge work flow

```
// "devel"이라는 분기를 만들고 체크 아웃합니다. 
// "devel"은 처음에 "master"분기와 동기화됩니다. 
$ git checkout -b devel 
      // 다음과 동일 : 
      // $ git branch devel 
      // $ git checkout

 // 편집 / 스테이지 / 커밋 
$ git add <file> 
$ git commit -m " commit-message " 

// 프로덕션 "마스터"브랜치로 "devel" 
$ git checkout master 
$ git merge devel 

// 두 브랜치를 원격 저장소로 푸시

 
$ git push origin master devel // "devel"브랜치를 체크 아웃하고 계속합니다 ...
   // Edit / Stage / Commit / Push 

// 프로덕션에서 버그를 수정해야합니다 ( "마스터"지점에서) 
$ git checkout master
// 버그를 수정하기 위해 "수정"분기를 생성하고 "마스터"분기와 병합합니다. 

// "devel"분기를 제거하려면 (분기가 동기화되지 않은 경우) 
$ git branch -d devel 
// To "devel"브랜치를 다시 만듭니다 
$ git checkout -b devel
```

####  "git-gui" "gitk"도구를 사용하여 커밋 그래프를 볼 수 있습니다 

![1573805264022](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1573805264022.png)

```
bash> $ git gui 
Repository tab 클릭
Visualize master's History 클릭
```

[atlassian]: https://www.atlassian.com/git/tutorials/making-a-pull-request



### 13.  Synchronizing Remote and Local: Fetch/Merge, Pull and Push

1. **git fetch**

  `git fetch`"명령은 로컬 작업 트리를 업데이트하지 않고 원격 저장소에서 로컬 저장소로 커밋을 가져옵니다. 

 이를 통해 작업 트리를 업데이트 (병합)하기 전에 변경 사항을 검토 할 수 있습니다.  

 페치 된 오브젝트는 원격 브랜치에 저장되며 로컬 브랜치와 구별됩니다. 

```
$ cd / path-to / working-directory
  
$ git fetch <원격 이름> 
   // 원격 저장소에서 로컬 저장소로 모든 지점을 
 가져옵니다.
    
$ git fetch <원격 이름> <branch-name> // 특정 지점을 가져옵니다. 원격 저장소에서 로컬 저장소로 

// 로컬 분기 나열 
$ git branch 
* master 
  devel // * 현재 분기 표시 // 원격 분기 나열 
$ git branch -r 
  origin / master 
  origin / devel // 원격 체크 아웃 가능 분기 파일 / 커밋을 검사합니다. 
// 그러나 이렇게하면 "분리 된 헤드"상태가되므로

// 원격 브랜치를 업데이트합니다. 

// 페치 된 변경 사항을 로컬 저장소에 병합 할 수 있습니다. 
$ git checkout master 
   // 로컬 리포지토리의 "마스터"브랜치로 전환 
$ git merge origin / master 
```

2. **git pull**

   `git fetch`와 `git merge`를 하나의 명령으로 결합.

   ```
   $ git pull <remote-name> 
      // 원격의 현재 브랜치 복사본을 가져 
      와서 로컬 리포지토리로 즉시 병합합니다 . 즉, 작업 트리를 업데이트합니다. 
      
   // 
   $ git fetch <remote-name> <current- 와 동일 branch-name> 
   $ git merge <원격 이름> <현재 지점 이름>
    
   $ git pull --rebase <원격 이름> 
      // 원격 지점 다음에 로컬 변경 사항을 선형화합니다.
   ```

   `git pull`을 사용하면 로컬 레포를 origin(또는 upstram) 변경 사항(특정 브렌치)과 동기화 할 수 있습니다.

   ![git fetch pull push에 대한 이미지 검색결과](http://www-creators.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-25-at-17.27.15.png)

   

3. **git push**  (revision)

   `git push <remote-name> <branch-name> `은 git fetch 로컬 저장소에서 원격 저장소로 커밋을 내보내는 종류의 일종

```
$ git push --set-upstream origin master

$ git push <원격 이름> <branch-name> 
   // 로컬 리포지토리의 특정 분기를 
 푸시
    
$ git push <원격 이름> --all // 로컬 리포지토리의 모든 분기를 
 푸시
    
$ git push <원격 이름 > --tag // 모든 태그 푸시 
   // "git push"는 태그를 푸시하지 않습니다
    
$ git push -u <remote-name> <branch-name> 
   // 원격 이름과 branch-name을 
   // 참조 로 저장합니다 (또는 현재) remote-name 및 branch-name. 
   // 인수가없는 후속 "git push"는 이러한 참조를 사용합니다.
```



### 14. fork 및 pull request

- "포크"버튼을 누르면 계정 (예 : 프로젝트 관리자)에서 자신의 개인 계정으로 프로젝트 를 *복사* 합니다. 

  

- "Pull Request"버튼을 눌러 다른 개발자 (예 : 프로젝트 관리자 또는 전체 프로젝트 팀)에게 변경 사항을 검토 하도록 *알립니다* . 승인되면 프로젝트 관리자가 변경 사항을 가져 와서 적용 할 수 있습니다. 풀 요청은 소스의 리포지토리 이름, 소스의 브랜치 이름, 대상의 리포지토리 이름 및 대상의 브랜치 이름을 제공해야합니다.



### 15.  Feature-Branch Workflow for Shared Repo

![기능 분기 워크 플로우](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_FeatureBranchWorkFlow.png)



### 16.  Forking Workflow

![Forking Workflow](https://www.ntu.edu.sg/home/ehchua/programming/howto/images/Git_ForkingWorkFlow.png)



### 17. Commit 이슈 

1. 마지막 커밋 수정

   ```
   $ git commit --amend -m "message"
   
   //예를 들어
   // 커밋을 수행합니다 
   $ git commit -m "added login menu" 
   
   // 일부 파일을 준비하지 않았 음을 인식합니다. 
   // 커밋 수정 
   $ git add morefile 
   $ git commit --amend 
       // 커밋 메시지를 수정할 수 있습니다.
   ```

   

2. 

3. 

4. 

5. 

6. 

7. 

8. 

9. 

10. 

11. 

12. 

13. 

14. 

15. 

16. 

17. 

18. 

19. 

    ```
    
    ```

    

    ! [remote rejected] master -> master (pre-receive hook declined) error: failed to push some refs to 'https://github.com/pillarorigin/hello-world.git'

    ```
    $ git lfs install
    ```

    Updated git hooks. Git LFS initialized.

    ```
    $ git lfs track "*.pdf"
    ```

    Tracking "*.pdf"

    ```
    $ git push origin master
    
    ```



###  **REFERENCES & RESOURCES** 

>1. GIT mother site @ [http://git-scm.com](http://git-scm.com/) and GIT Documentation @ http://git-scm.com/doc.
>2. Git User's Manual @ http://www.kernel.org/pub/software/scm/git/docs/user-manual.html.
>3. Git Hosts: GitHub @ [https://github.com](https://github.com/), Bitbucket @ [https://bitbucket.org](https://bitbucket.org/).
>4. Git Tutorials @ https://www.atlassian.com/git/tutorials.
>5. Bitbucket Documentation Home @ https://confluence.atlassian.com/display/BITBUCKET/Bitbucket+Documentation+Home.
>6. Bitbucket 101 @ https://confluence.atlassian.com/display/BITBUCKET/Bitbucket+101.
>7. Jon Loeliger and Matthew McCullough, "Version Control with Git", 2nd Eds, O'reilly, 2012.
>8. Scott Chacon, "Pro Git", Apress, 2009.
>9.  https://www.ntu.edu.sg/home/ehchua/programming/howto/Git_HowTo.html
>10.  https://parksb.github.io/article/28.html 
