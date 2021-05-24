# JPA를 사용해야하는 이유

- SQL 중심적 개발에서 → 객체 중심적 개발
- 생산성
- 유지보수

패러다임의 불일치 해결

1. 상속
2. 연관관계
3. 객체 그래프 탐색

성능 최적화 기능

1. 1차 캐시와 동일성 보장

    db isolation level이 Read Commit 이어도 애플리케이션에서 Repeatable Read 보장

    같은 트랜잭션 안에서는 같은 엔티티 반환 - 약간의 조회 성능 향상

    ```java
    String memberId = "100";
    Membmr m1 = jpa.find(Member.class, memberId); //SQL
    Membmr m2 = jpa.find(Member.class, memberId); //캐시
    println(m1 == m2) //true
    //동일한 키로 조회할 경우
    //아주 짧은 캐싱이 이루어져 성능향상이 이루어짐
    ```

2. 트랜잭션 지원하는 쓰기 지연

    트랜잭션을 커밋할 때가지 INSERT SQL을 모음

    JDBC BATCH SQL 기능을 사용해서 한번에 SQL전송

    ```java
    transaction.begin(); //트랜잭션 시작
    em.persist(memberA);
    em.persist(memberB);
    em.persist(memberC);
    transaction.commit(); //트랜잭션 커밋
    ```

3. 지연 로딩과 즉시 로딩

    **지연 로딩**

    객체가 실제 사용될 때 로딩

    ```java
    Member member = memberDAO.find(memberId); -> SELECT * FROM MEMBER...
    Team team = member.getTeam();
    String teamName = team.getName(); -> SELECT * FROM TEAM ...
    ```

    위와 같이 team.getName()을 호출하는 순간 마법같이 그부분의 쿼리를 다시 태워서 필요할 때만 사용 할 수 있다.

    **즉시 로딩**

    JOIN SQL로 한번에 연관된 객체까지 미리 조회

    ```java
    Member member = memberDAO.find(memberId); -> SELECT M.*, T.* FROM MEMBER JOIN TEAM...
    Team team = member.getTeam();
    String teamName = team.getName(); 
    ```

    하지만 개발을 하다보니 member를 조회할 때는 항상 team을 사용하는경우가 있을 수 있다.

    그렇다면 계속해서 쿼리를 2번 타는경우가 생기는데 JPA에서는 옵션하나로 이러한 부분을 바꿔줘

    조회할 때 항상 해당하는 곳을 조인시켜오게 만들 수 있어 성능최적화에 도움이 될 수 있다.

데이터 접근 추상화와 벤더 독립성

여담으로 JAVA 표준이기도 하다.
