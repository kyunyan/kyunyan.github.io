# Reset, Revert 

Reset은 Remote 저장소에서 reset을 하기에는 문제가 있기때문에 어떤 특정 버전이 문제가 있다고 가정될시 Remote저장소에서 지우려고 하면 Revert 를 해야한다.

1. reset

- git reset --hard 
git reset --hard 커밋아이디를 통해 현재 가고싶은 이전버전으로 돌릴수도있다.
다만 현재 진행중인 워킹디렉토리가 사라지니 주의 해야된다.

- git reset --mixed 
커밋한 내용을 없애고 그 내용이 unstaged 상태로 돌아감

- git reset --soft 
커밋한 내용을 없애고 그 내용을 staged 상태로 돌아감

2. revert

git revert (되돌릴 커밋 해시)

git revert --continue

커밋되징낳은 상태로 되돌린다
git revert --no-commit (되돌릴 커밋 해시)

소스트리로 리버트는 커밋 되돌리기



