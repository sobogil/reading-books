## 📝 목차
- [Chapter15](#Chapter15)

## Chapter15 간단한 웹 어플리케이션의 구조

1. 간단한 웹 어플리케이션의 구성 요소

프론트 서블릿, 건트롤러 + 뷰, 서비스, DAO

스프링 MVC에서는 DispatcherServlet이 프론트 서블릿의 역할을 한다.
컨트롤러는 실제 웹 브라우저의 요청을 처리한다. 컨트롤러의 주요 역할은
-클라이언트가 요구한 기능을 실행 
-응답 결과를 생성하는데 필요한 모델 생성
-응답 결과를 생성할 뷰 선택

서비스는 기능의 로직을 구현한다. 사용자의 비밀번호 변경에서 핵심 로직은 비밀번호를 바꾸는 행위이며 폼이나 뷰를 보여주는 것은 핵심 로직이 아니다.

DAO를 사용해서 서비스와 데이터 베이스를 연동한다.

