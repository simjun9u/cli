## 0. 요약
* Git 설치
* Project 생성
	* 로컬→ 깃허브 : 원칙은 이런데 (Github 없어도 쓸 수 있는 것이 Git인데), 
	* 깃허브→ 로컬 : 협업하다 보면 (전문가의 코드를 내려받다 보면), 여기에 더 익숙해짐. 
* Code 수정
	* ㅁㄴㄹ
* ㅁㄴㄹ

### 0-1. 역사 (납득)

**Git blame** (blame: ~을 탓하다. 비난하다.)
```shell
git blame <파일명>
```
* 문제 발생시, 책임 소재 파악(마녀사냥)하기 위한 기능. 
  '커밋, 이름, 시간'을 띄워 문제에 대해 가장 잘 아는 전문가(버그 유발자)를 호출.
* 잘못된 부분만 롤백할 수 있도록 (잡도리를 피하거나, 딱 잘못한 만큼만 잔소리 듣도록), 
  git 기능이 복잡한 이유를 납득하고, 잘 사용해 보자. 
* 역사:
	* 1990 CVS : `cvs annotate` (의도)
	* 2000 TortoiseCVS (GUI) : `Finding Out Who to Blame` (용도)
	* 2000 SVN : `svn annotate` 및 `svn blame` 및 `svn praise` (태도)
	  당신의 상사가 코드를 짜서 내 어깨 너머로 지켜보고 있다면 svn praise를 사용하세요. 
	* 2005 Git : `git blame` (법도) 
	  ??? : parise 그런 거 없다.

**Git 이전의 버전 관리 시스템과 차이** (어쩌면 창시자 빡침 포인트)
* CVS (Concurrent Versions System) - 파일단위 버전관리
* SVN (Subversion) - 커밋단위 버전관리 (파일이동, 이름변경 가능. Metadata 폴더 `.svn` 관리)
* Git (리누스 바보) - SVN 대비 빠른성능, 분산처리(서버 아닌 로컬 관리. 비행기에서 작업가능.).
	* `commit`: 작업(롤백) 단위. 서버전송 아닌, 로컬기록. diff 아닌, 스테이지snapshot 기록.
	* `add`: 대상 추가. 초기 일회성 버전관리대상 등록 아닌, 매번 변경사항 스테이지에 추가. 
	  즉, 수정·추가·이동·삭제 등 변경사항 또는 작업단위 별 일부 변경사항을 commit 전 모음.
	  여러번 `add`해서 스테이징 가능. `add`후 수정시, 수정파일 재차`add`해서 스테이지 갱신. 
	  `git restore --staged`해서 스테이지 제외 가능. 
	  (실익: 프론트·백엔드 수정한 것을 나눠서 각각 따로 커밋하면 롤백·수정 범위 명확해짐) 
	  (현실: `git add .` 로 편리하게 무지성 스테이징. 내일의 문제는 내일의 내 일)
	* `checkout`: 보관소에서 내 작업 공간으로 (도서관 대출). 
	  서버에서 PC로 처음 일회성 일괄 파일다운 아닌, (다른branch, 과거상태) 작업환경 전환.
	  `git clone`: 처음 일회성 일괄 파일다운. 
	* `revert`: 원복. 흔적 없는 과거 원본 복귀(구 버전번호) 아닌, 흔적 있는 커밋(신 버전번호).
	  수정사항 철회할 때, 중간버전 받고 수정중인 협업자들과 버전충돌 방지 위함. 
	  `git reset --hard` 및 `git restore`: 손상 복구. 흔적 없는 과거 복귀(구 버전번호). 
	* 버전관리
		* SVN: (Diff·Delta) 첫 버전 저장 후 매 버전 사이 변경된 부분만 증분 저장.
		  장점: (HDD 40~80GB) 용량 절약. 단점: 버전이 많아지면 연산량 급증 및 속도 저하. 
		* Git: (Snapshot) 매번 스테이징 전체를 압축 커밋하되, 미변경사항은 구버전 포인팅. 
		  장점: Version이동·Branch전환 속도 매우 빠름. **단점: 어렵다Git.** 
	* 서버와 동기화
		* `svn update`: 서버 최신코드→ 로컬 작업공간 덮어쓰기. `svn checkout` 이후 수행.  
		* `git update`: 없음. fetch→ pull 2단계로 수행
		* `git fetch`: 서버 변경이력 확인. 
		* `git pull`: '원격' 코드를 내 로컬 코드에 병합(merge)
	* 브랜치 병합
		* `svn merge`: 작업 폴더에 브랜치 가져와 합집합. (이후 `svn commit` 따로 해야함)
			* 충돌시/삭제시: 자세한 설명은 생략한다. 
		* `git merge`: 현재branch에 다른branch를 병합. (기능개발 후 메인에 병합커밋)
			* 2-합집합 아닌, 3-way-merge(Base공통조상/Branch1/Branch2 비교 병합)
			  (Base=Branch1인 경우, 포인터만 옮기는 상황 등도 있음.)
			* Conflict: 두 Branch가 같은 파일 '같은 줄(Line)'을 서로 다르게 수정시 충돌.
			  충돌시 병합커밋 안 함. 미완료·작업중 상태 유지. 
			* `git status`: 충돌한 파일 확인 가능.
			* `<<<<<<< 1현재브랜치코드 ======= 2가져온코드 >>>>>>>` 영역 수정. 
			* 충돌 이후 `git add <수정 완료된 파일명>` 후 `git commit` 해야 문제해결 완료.
			* `git merge --abort`: 망했을 경우, 복구(restore, 흔적 없음).
	* 브랜치 생성
		* `svn copy`: SVN은 브랜치 체계 없음. 단순히 다른 폴더에 복사본 생성 후 작업. 
		* `git branch` 및 `git switch -c` : 복사 아닌 포인터 생성. 빠름.
			* 전환명령에 생성 파라미터 (최신 `git switch -c`, 예전 `git checkout -b`)
		* (참고) 관습적 브랜치명
			* `main`: 기본 branch. (구 `master`: 노예문제 용어회피.)
			* `origin`: 원격 repo. (`git push http:~.git main`→ `git push origin main`)
			* upstream: origin(fork proj 경우)의 원본 프로젝트 저장소.
	* 긷 (샘·우물·허브의 물·소스를 바가지로 퍼가요) 아님.  
 

## 1. Git 시작
### 1-1. Git 설치
* Git 설치
* Git 설치된 폴더
	* 프로그램 폴더: `C:\Program Files\Git` 및 `/usr/local/git` 등
	* 프로젝트 폴더: `%ProjFolder%` ㅁㄴㅇㄹ

### 1-2. Git Config 환경설정
```sh
# 코드 수정할 사람(미래의 blame 받을 나) 등록. 아래 명령 각각 실행
git config --global user.email "본인의GitHub이메일@example.com"
git config --global user.name "본인의GitHub닉네임"
```

```sh
# LF will be replaced by CRLF 줄바꿈(리눅스맥/윈도우) 자동변환 주의경고 대응. 
git config --global core.autocrlf true
```

```sh
# 모든 설정값 확인
git config --list

# 개별값 확인
git config --global user.email
git config --global user.name
```

## 2. Project 생성
### 2-1. Git Init

### 2-2 Github Repo 생성 및 Clone

```sh
git clone https://github.com/simjun9u/cli.git
```

## 3. Pull (Github→ Local) & 
### 3-1. Git pull

```sh
cd cli
git pull
```

다른 사람이 수정했거나, 다른 기기에서 올린 최신 코드가 있을 수 있음. 내 컴퓨터의 상태를 GitHub 서버와 똑같이 맞춰두지 않고 수정을 시작하면, 나중에 코드가 충돌(`Conflict`)하여 업로드가 막힐 수 있음.


### 3-2. 파일 수정 및 작업 진행
* **행동:** 메모장, VS Code 등 원하는 편집기로 폴더 내의 파일을 수정하거나 새 파일을 생성함.

### 3-3. 수정된 파일 확인
* 
cmd

```sh
git status
```

해야 하는 이유: 내가 어떤 파일을 수정했고, 어떤 파일이 새로 추가되었는지 현재 상태를 모니터링하여 실수로 원치 않는 파일이 올라가는 것을 방지함.
* git pull 이후* 시점: 다른 사람의 코드를 받고 내 작업을 새로 시작하기 전, 또는 코딩을 마친 직후

입력하는 이유: * 코딩 시작 전: 내 현재 폴더가 깨끗한 상태(Clean)인지 확인하여 이전 작업과 꼬이는 것을 방지함.

코딩 마친 후: 내가 오늘 어떤 파일들을 건드렸는지 목록을 눈으로 확인하고 기억하기 위함.

2. git add . 실행 직전과 직후 (가장 중요)
시점: [수정 완료] -> git status -> git add . -> git status

입력하는 이유:

add 전: 올라가면 안 되는 임시 파일이나 비밀번호가 적힌 설정 파일 등이 수정 목록(빨간색)에 포함되어 있는지 검사함.

add 후: 내가 올리려던 파일들이 장바구니(초록색)에 안전하게 잘 담겼는지 최종 확인하기 위함. 이 단계를 거쳐야 실수로 엉뚱한 파일을 커밋하는 일을 막을 수 있음.

3. git commit 실행 직후 ~ git push 전
시점: git commit -m "..." -> git status -> git push

입력하는 이유: * 커밋이 성공했다면 git status 결과창에 초록색 글씨가 모두 사라지고 "nothing to commit, working tree clean"이라는 메시지가 떠야 함.

동시에 "Your branch is ahead of 'origin/main' by 1 commit." (서버보다 내 컴퓨터가 1개 커밋만큼 앞서 있다)라는 메시지를 확인하여, 이제 push만 하면 되는 타이밍임을 확신할 수 있음.

```sh
# 스테이징 전부
git add .

# 스테이징 일부
git add ㅁㄴㅇㄹ
```



```sh
git commit -m "수정완료"

# 귀차니즘 (add 통합)
git commit -a
```

```sh
git push origin main
```

```sh
1. git pull                  (최신 코드 가져오기)
2. (메모장이나 도구로 파일 수정 작업 진행)
3. git status                (내가 뭘 바꿨지? 빨간색 파일 확인)
4. git add .                 (장바구니에 담기)
5. git status                (잘 담겼나? 초록색으로 변했는지 확인)
6. git commit -m "수정완료"   (로컬 저장소에 기록)
7. git status                (내역이 깔끔하게 비었는지, push 대기 상태인지 확인)
8. git push origin main      (GitHub 서버로 최종 업로드)
```
## Ref.
* asdf
* aa