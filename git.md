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
    // 커밋에 사용되는 사용자 이름과 이메일을 설정합니다. 
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
6. git help <command> or git <command> -- help : 도움말
[git mother site]: https://git-scm.com/docs


### 7. Git Storage Model
[사진 첨부 # Git_StorageDataFlow.png]


### 8. Git 로컬 repo 시작
git 프로젝트 시작 방법은 2가지가 존재합니다.
    1. 자신의 프로젝트 새로 시작
    2. Git host에서 기존 프로젝트 복제(clone)

1. 자신의 프로젝트 새로 시작
    1) 새로 시작 시 디렉토리 설정.
    자신의 프로젝트를 설명하기 위한 "README.md"파일 을 작성하는게 좋습니다.
    (Markdown구문의 텍스트 파일을 제공하는 것이 더 좋습니다)
    [MarkDown]: https://help.github.com/en/github/writing-on-github

    2) 새로운 git repo를 초기화 (해당 프로젝트 디렉토리로 들어가서 초기화해야 합니다.
    ```
    $ cd / 해당하는 프로젝트 경로/
    $ git init
    ```
    git init 명령어를 입력한 뒤에 해당하는 local repo는 비어있어야 합니다. 
    파일을 명시적으로 repo에 deposit해주어야 합니다.
    (Before we proceed, it is important to stress that Git manages changes to       files between so-called commits. In other words, it is a version control        system that allows you to keep track of the file changes at the commits.
    





```
$ git remote add git 
remote add [<options>] <name> <url>

    -f, --fetch           fetch the remote branches
    --tags                import all tags and associated objects when fetching
                          or do not fetch any tag at all (--no-tags)
    -t, --track <branch>  branch(es) to track
    -m, --master <branch>
                          master branch
    --mirror[=(push|fetch)]
                          set up remote as a mirror to push to or fetch from

```



```
$ git remote add origin <URL>
```



```
$ git remote -v
```



```
$ git pull
```

master branch pull



```
$ get add .
```

index



```
$ git status
```

On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)



```
$ git commit -m "file name"
```



```
$ git status
```

On branch master
nothing to commit, working tree clean



```
$ git push origin master
# git push --set-upstream origin master
```

fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

...

 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'https://github.com/pillarorigin/hello-world.git'

    $ git lfs install

Updated git hooks.
Git LFS initialized.



```
$ git lfs track "*.pdf"
```

Tracking "*.pdf"



```
$ git add . 
```



```
$ git commit -m "commit message"
```



```
$ git push origin master
```

[출처] : https://www.ntu.edu.sg/home/ehchua/programming/howto/Git_HowTo.html
