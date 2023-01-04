# branch

### branch 생성

1. branch 생성

git branch 브런치 이름


2. 브런치 목록 인

git branch

3. 브런치 이동

git switch 브런치 이름

4. 브런치 생성과 동시에 이동

git switch -c 브런치 이름

5. 브런치 삭제

git branch -D 브런치 이름

6. 브런치 이름 변경

git branch -m 기존 브런치 이름 새로운 이름

7. 여러 브런치 내역 편하게 보기
git log --all --decorate --oneline --graph

### merge VS Rebase 

1. merge 로 합치기
메인 브랜치에서 특정 브랜치를 합칠때 메인 브랜치로 이동한 후

git merge 특정브랜치 

2. Rebase 로 합치기

특정 브랜치와 메인 브랜치를 합칠때
특정 브랜치로 이동후 메인 브랜치를 rebase 한다.

git rebase master

하면 특정브랜치 스냅샷이 더 앞에 있을텐대
마스터 브랜치 이동후 특정브랜치를 머지로 합처준다

### merge, rebase 충돌시 

1. merge 충돌시
머지 충돌시 충돌 해결 후 에드 커밋 해주면 된다.

당장 해결 불가능할시 
git merge --abort

2. rebase 충돌시
리베이스 충돌시 에드 후
git rebase --continue

당장 해결 불가능할시 
git rebase --abort