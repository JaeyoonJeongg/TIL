
# 커넥션 풀과 데이터소스

####

#### 커넥션 풀

- 데이터베이스 커넥션을 획득하는 과정

    1. 애플리케이션 로직은 DB 드라이버를 통해 커넥션 조회

    2. DB 드라이버는 DB와 TCP/IP 커넥션 연결

    3. TCP/IP 커넥션 연결되면 id, pw와 부가정보를 DB에 전달

    4. DB는 id, pw를 통해 내부 인증 완료, 내부에 DB 세션을 생성

    5. DB는 커넥션 생성이 완료되었다는 응답 보냄

    6. DB 드라이버는 커넥션 객체를 생성해서 클라이언트에 반환함.


- 이런 복잡하고 시간이 많이 소요되는 문제를 해결하는 아이디어가 커넥션 풀


- 커넥션 풀 초기화

    - 애플리케이션을 시작하는 시점에 커넥션 풀은 필요한 만큼 커넥션을 미리 확보

    - 보통 기본값으로 10개를 보관함

- 커넥션 풀 연결상태

    - TCP/IP로 DB와 커넥션이 연결되어 있는 상태이기 때문에 언제든지 즉시 SQL을 DB에 전달할 수 있음.


- 커넥션 풀 사용1

    - 이미 생성되어 있는 커넥션을 객체 참조로 그냥 가져다 쓰면 됨

    - 커넥션 풀에 커넥션을 요청하면 하나를 반환받을 수 있음.

- 커넥션 풀 사용2

    - 커넥션 풀에서 받은 커넥션 사용해 SQL을 데이터베이스에 전달하고 그 결과를 받아서 처리함

    - 커넥션을 모두 사용하고 나면 커넥션을 종료하는 것이 아니라, 다음에 다시 사용할 수 있도록 해당 커넥션을 그대로 커넥션 풀에 반환하면 됨

    - 커넥션을 종료하지 않고 살아있는 상태로 반환해야 함.


** 커넥션 풀은 이점이 크기 때무에 실무에서 항상 기본으로 사용함 **

- 오픈소스 커넥션 풀 사용하면 좋음

- 예) commons/dbcp, tomcat-jdbc pool, hikariCP

- 대부분 hikariCP 사용


#### DataSource

- DataSource는 커넥션을 획득하는 방법을 추상화 하는 인터페이스.
- DataSource의 핵심 기능
```java
public interface DataSource {
    Connection getConnection() throws SQLException;
}
```
- 대부분의 커넥션 풀은 DataSource 인터페이스를 이미 구현해둠
- 커넥션 풀 구현 기술을 변경하고 싶으면 해당 구현체로 갈아끼우면 됨
- Driver Manager는 DataSource 인터페이스 사용하지 않음