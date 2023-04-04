
# 커넥션 풀과 데이터소스

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

**커넥션 풀은 이점이 크기 때무에 실무에서 항상 기본으로 사용함**

- 오픈소스 커넥션 풀 사용하면 좋음
- 예) commons/dbcp, tomcat-jdbc pool, hikariCP
- 대부분 hikariCP 사용

#### DataSource

- DataSource는 **커넥션을 획득하는 방법을 추상화** 하는 인터페이스
- DataSource의 핵심 기능 : 커넥션 조회 (다른 기능들은 중요하지 않음)
```java
public interface DataSource {
    Connection getConnection() throws SQLException;
}
```
#### DataSource 정리
- 대부분의 커넥션 풀은 DataSource 인터페이스를 이미 구현해둠
- 커넥션 풀 구현 기술을 변경하고 싶으면 해당 구현체로 갈아끼우면 됨
- DriverManager는 DataSource 인터페이스 사용하지 않음
- 스프링에서는 DriverManager가 Datasource를 통해서 사용할 수 있도록 DriverManegerDataSource를 제공함
- 자바는 DataSource를 통해 커넥션을 획득하는 방법을 추상화햤기 때문에 애플리케이션 로직은 DataSource 인터페이스에만 의존하면 된다.
``` java
void dataSourceDriverManager() throws SQLException {
        //DriverManagerDataSource -> 항상 새로운 커넥션을 획득
         DriverManagerDataSource dataSource = new DriverManagerDataSource(URL, USERNAME, PASSWORD);
          useDataSource(dataSource);
     }

     private void useDataSource(DataSource dataSource) throws SQLException {
        Connection con1 = dataSource.getConnection();
        Connection con2 = dataSource.getConnection();
        log.info("connection={}, class={}",con1, con1.getClass());
        log.info("connection={}, class={}",con2, con2.getClass());
     }
```
- DriverManager는 커넥션을 획득할 때 마다 URL, USERNAME, PASSWORD 같은 파라미터들을 계속 전달해야함.
- DataSource는 처음 객체 생성할때만 필요한 파라미터를 넘겨둠.

#### 설정과 사용의 분리
- 설정
  - DataSource를 만들고 필요한 속성들을 사용해서 URL, USERNAME, PASSWORD 같은 부분들을 입력하는 것
- 사용
  - 설정은 신경쓰지 않고, DataSource의 getConnection()만 호출해서 사용하면 됨.

#### 설정과 사용의 분리 설명
- Repository는 DataSource만 의존하고 다른 속성들을 몰라도 됨.
- 객체를 설정하는 부분, 사용하는 부분을 명확하게 분리할 수 있음.
 