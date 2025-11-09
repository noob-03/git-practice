깃 스터디 - 챕터 2 정리

🔹 깃으로 버전 관리하기

📑 목차

[1] 깃 저장소 만들기

[2] 버전 만들기

[3] 커밋 내용 확인하기

[4] 버전 만드는 단계마다 파일 상태 알아보기

[5] 작업 되돌리기

[6] 문제 풀이

[1] 깃 저장소 만들기

 사용자 컴퓨터에 저장소 만들기

1️⃣ 새로운 디렉터리 생성

터미널에서 다음 명령을 입력한다.

mkdir hello-git
cd hello-git


홈 디렉터리에 hello-git 디렉터리를 생성하고 해당 디렉터리로 이동한다.

2️⃣ 디렉터리 안 내용 확인

ls -la


숨김 파일을 포함한 디렉터리 내 파일 목록을 확인한다.

3️⃣ 마침표의 의미

. : 현재 디렉터리

.. : 상위 디렉터리

4️⃣ 디렉터리 초기화

git init


현재 디렉터리를 Git 저장소로 초기화한다.

명령 실행 후 .git이라는 숨김 폴더가 생성되면 완료.

[2] 버전 만들기
📘 깃에서 버전이란?

문서를 수정하고 저장할 때마다 생기는 변경 이력(스냅샷) 을 의미한다.
파일명을 매번 바꾸지 않아도, 변경 내용과 시간을 모두 기록할 수 있다.

스테이지와 커밋 이해하기
구분	설명
작업 트리 (Working Directory)	실제로 파일을 수정, 저장하는 디렉터리
스테이지 (Staging Area)	버전으로 만들 파일을 대기시켜두는 공간
저장소 (Repository)	스테이지에 있던 파일들이 커밋되어 기록되는 공간
🪜 버전 생성 과정

1️⃣ 파일 수정

vim hello.txt


2️⃣ 수정된 파일 스테이징

git add hello.txt


3️⃣ 커밋으로 버전 생성

git commit -m "첫 번째 커밋"


4️⃣ 상태 및 로그 확인

git status
git log


📌 git commit -am "메시지" 명령을 사용하면 스테이징과 커밋을 한 번에 수행할 수 있다.

[3] 커밋 내용 확인하기
🧾 커밋 로그 확인
git log


commit 옆의 긴 문자열은 커밋 해시(commit hash) 라고 하며, 각 커밋을 구별하는 고유 식별자이다.

(HEAD -> main) 은 현재 최신 커밋임을 의미한다.

Author, Date, Message 정보가 함께 표시된다.

변경 사항 비교
git diff


작업 트리 ↔ 스테이지

스테이지 ↔ 저장소
이 둘 간의 차이를 비교한다.
삭제된 줄은 -, 추가된 줄은 +로 표시된다.

[4] 버전 만드는 단계마다 파일 상태 알아보기

파일 상태 구분
상태	설명
untracked	한 번도 커밋하지 않은 새 파일
tracked	커밋한 적 있는 파일로, Git이 변경 사항을 추적함
git status


working tree clean → 모든 파일이 unmodified 상태

Changes not staged for commit → modified 상태

Changes to be committed → staged 상태

📌 커밋 후에는 다시 unmodified 상태로 돌아감.

기타 명령
git log --stat


각 커밋별로 변경된 파일의 통계 확인 가능.

vim .gitignore


버전 관리에서 제외할 파일/디렉터리를 지정할 수 있다.

[5] 작업 되돌리기
🪄 작업 트리 되돌리기
git restore hello.txt


작업 디렉터리에서 수정한 파일을 가장 최근 커밋 상태로 되돌린다.

스테이징 되돌리기
git restore --staged hello.txt


스테이징된 파일을 취소하고, 수정 파일을 다시 작업 트리 상태로 되돌린다.

최신 커밋 되돌리기
git reset HEAD^


가장 최근 커밋을 취소한다.

--soft : 커밋만 취소, 스테이징 상태 유지

--mixed : 커밋 취소 + 스테이징 해제

--hard : 커밋과 수정 내역 모두 삭제

특정 커밋으로 되돌리기
git reset --hard [커밋 해시]


지정한 커밋으로 돌아가며, 이후 커밋들은 삭제된다.

커밋 이력 취소하기 (되돌리되 기록은 남김)
git revert [커밋 해시]


변경 내용만 되돌리고, 되돌렸다는 새로운 커밋을 생성한다.

[6] 문제 풀이

번호	명령어	설명

1	git config --global user.name "easys"	사용자 이름 설정

2	git config --global user.email "doit@easys.co.kr"	이메일 설정

3	git init	저장소 초기화

4	git status	파일 상태 확인

5	git add ch01.txt	파일 스테이징

6	git commit -m "ch01"	커밋 생성

7	git commit -am "ch02"	수정 + 커밋 한 번에

8	git log	커밋 로그 확인

9	git diff	변경 사항 비교
10	git restore work.txt	파일 수정 취소
11	git restore --staged work.txt	스테이징 취소
12	git reset HEAD^	최신 커밋 취소
13	git reset --hard [해시]	특정 커밋으로 복원
14	git revert [해시]	변경 내용 취소, 새 커밋 생성
