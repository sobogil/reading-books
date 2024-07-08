## 📝 목차
- [Chapter13](#Chapter13)

## Chapter13 MVC 3: 세션, 인터셉터, 쿠키

## 로그인 과정
AuthInfo클래스로 회원 정보를 저장하고 Member클래스로 회원 정보를 받는다. 
AuthService클래스에서 Member클래스로 받은 회원정보를 AuthInfo에 저장하고, LoginController에서 Service클래스의 메서드를 사용해서 로그인 성공 혹은 실패 페이지로 이동하게 한다.

다음 할 작업은 컨트롤러와 서비스를 스프링 빈으로 등록하는 것이다.

3. 컨트롤러에서 HttpSession사용

로그인 상태를 유지하기 위해선 Httpsession을 사용하거나 쿠키를 사용하는 방식을 사용한다.

컨트롤러에서 httpSession을 사용하려면 요청매핑 어노테이션 적용 메서드에 Httpsession 파라미터를 추가한다.
요청 매핑 어노테이션에 HttpServletRequest 파라미터를 추가하고 HttpServletRquest를 이용해서 HttpSession을 구한다. 

4. 비밀번호 변경 기능 구현

command 객체와 validator클래스를 작성하고 컨트롤러에서 httpsession에 authinfo속성을 사용한다. 컨트롤러 처리 결과를 보여줄 Form 뷰와 Pwd뷰를 작성한다. 마지막으로 controllerConfig 설정에 컨트롤러를 빈으로 등록해준다.

이렇게 만들면 생기는 문제점은 서버를 재시작하면 로그인을 다시해야한다. 
session.getAttribute()에서 서버를 재시작하면 null을 리턴하며 NullPointException이 발생하게 된다.

5.인터셉터 사용하기 

로그인하지 않은 상태에서 get방식으로 주소창에 uri를 치면 해당 폼으로 넘어가게 된다. 그러므로 httpSession 확인코드를 삽입해야한다. 하지만 실제 웹에서는 많은 확인코드를 넣어야하므로 이렇게 다수의 컨트롤러에 동일한 기능을 적용할때 사용하는 것이 HandlerInterceptor이다.


