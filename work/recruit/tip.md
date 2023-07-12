### Spring MessageSource

```html
<label>이메일</label>
<input type="text" name="email">
```
- 문제점
1. 해당 문자열을 전부 '이메일 주소'로 바꿔야 할 경우
2. 다국어 지원 불가

이를 해결하기 위해서 *Spring MessageSource* 를 사용한다.
- 사용방법:
- 문자열을 담은 메시지 파일을 작성한다.
- 메시지 파일에서 값을 읽어오는 MessageSource 빈을 설정한다.
- JSP 코드에서 <spring:message> 태그를 이용해서 메시지를 출력한다.


1.Java의 .properties 작성 (src/main/resources/message/label.properties)
```properties
# label.properties
member.register=회원가입
 
term=약관
term.agree=약관동의
next.btn=다음단계
 
member.info=회원정보
email=이메일
name=이름
password=비밀번호
password.confirm=비밀번호 확인
register.btn=가입 완료
 
register.done={0}님, 회원가입을 완료하였습니다.
 
go.main=메인 화면으로 이동
```

2. MessageSource 빈 추가
```java
@Bean
public MessageSource messageSource() {
        var messageSource = new ReloadableResourceBundleMessageSource();
        messageSource.setBasename("classpath:/messages");
        messageSource.setDefaultEncoding("utf-8");
        messageSource.setCacheSeconds(3); //3초로 properties를 refresh 해줌.

        return messageSource;
        }
```
3. jsp 작성
```html
<%@ taglib prefix="spring" uri="http://www.springframework.org/tags" %>
 
<head>
    <title><spring:message code="member.register" /></title>
</head>
<body>
    <h2><spring:message code="term" /></h2>
    
    <!-- 아래도 마찬가지로 위처럼 작성하면 된다. -->
</body>
```

- 캐시 refresh가 안되는 경우, 이클립스 서버 clear 
