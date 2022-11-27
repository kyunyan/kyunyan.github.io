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