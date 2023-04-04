# JDBC
- JDBC 표준 인터페이스
- JDBC (Java Database Connectivity) 는 자바에서 데이터베이스에 접속할 수 있도록 하는 자바 API
- 데이터베이스에서 자료를 쿼리하더나 업데이트하는 방법 제공

#### JDBC 기능
- 연결: java.sql.Connection
- SQL 담은 내용: java.sql.Statement
- SQL 요청 응답: java.sql.ResultSet

#### JDBC 드라이버 (Mysql JDBC 드라이버, Oracle JDBC 드라이버)
- JDBC 인터페이스를 각각 DB에 맞도록 구현한 라이브러리


#### JDBC 장점
1. 데이터베이스를 다른 종류의 데이터베이스로 변경하면 애플리케이션 서버의 데이터베이스 사용 코드도 함께 변경해야 하는 문제
- DB를 다른 종류의 DB로 변경하고 싶으면 JDBC 구현 라이브러리만 변경하면 됨. 애플리케이션 서버의 사용 코드를 그대로 유지가능

2. 개발자가 각각의 데이터베이스마다 커넥션 연결, 그리고 그 결과를 응답 받는 방법을 새로 학습해야 하는 문제
- 개발자가 JDBC 표준 인터페이스 사용법만 학습하면 됨.

**그러나 DB를 변경하면 JDBC 코드는 변경하지 않아도 되지만 SQL은 해당 DB에 맞도록 변경해야 함.**
-> JPA (Java Persistence API) 사용하면 문제 해결 가능

#### SQL Mapper
- JDBC를 편리하게 사용하도록 도와줌.
- 예) 스프링 JdbcTemplate, Mybatis

#### ORM 기술
- 객체를 관계형 데이터베이스 테이블과 매핑해주는 기술.
- 개발자는 반복적인 SQL을 직접 작성하지 않고, ORM 기술이 SQL을 동적으로 만들어 실행해줌.
- 예) JPA, 하이버네이트, 이클립스링크


#### SQL Mapper vs ORM 기술
- SQL Mapper는 SQL만 직접 작성하면 됨. ORM 기술은 SQL 자체를 작성하지 않아도 돼 개발 생산성이 높아지지만 쉬운 기술이 아니라 깊이있는 학습이 필요함.

