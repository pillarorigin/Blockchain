### 1. push error
error: failed to push some refs to 'https://github.com/pillarorigin/Study_YIG.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

원인: Conflict (remote 버전과 로컬의 버전이 달라서 충돌난 경우)
해결: Merge (remote에 있는 변경 사항을 pull로 받은 뒤, 내 파일과 merge하고, 다시 push)


### 2. pull error
 * branch            master     -> FETCH_HEAD
fatal: refusing to merge unrelated histories

원인: github.com(원격저장소에서 추가한 커밋 내용)에서 새로 만들어진 파일(혹은 기타 커밋내용)이 로컬 저장소의 커밋 로그에 없어서 발생하는 error
    1. 원격저장소(github.com)의 master에서 로컬 저장소(dir)의 FETCH_HEAD를 merge하는 것이 거부된 상태
    2. pull 명령어는 fetch + merge 작업을 동시에 처리하는 명령어.
    3. 현 상황은 fetch는 되었지만, merge가 되지 않은 상태.
    4. fetch는 원격 저장소(github.com)에 있는 내용을 가지고 오지만 내 로컬저장소(dir)에는 merge 하지 않음.
       원격 저장소의 내용을 확인만 하고 로컬에 merge하고 싶지 않은 경우 fetch 명령어 사용.
       HEAD에는 가장 마지막에 행해진 commit정보가 담기므로 FETCH_HEAD는 원격 저장소의 최신 commit이력 존재
    5. pull은 git fetch + merge FETCH_HEAD임.
해결: fetch나 pull 명령어로 원격 저장소의 마지막 commit을 로컬 저장소의 commit 로그의 맨 앞으로 받아온다.
        1. git clone 명령어를 통해 원격 저장소를 복제.
        2. pull 명령어에 강제로 pull하는 옵션을 추가한다.
            ```$ git pull origin <branchName> --allow-unrelated-histories```
 
 ### 3. 
       
