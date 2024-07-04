## 📝 목차
- [Chapter13](#Chapter13)

## Chapter13 MVC 3: 세션, 인터셉터, 쿠키

# 로그인 과정
AuthInfo클래스로 회원 정보를 저장하고 Member클래스로 회원 정보를 받는다. 
AuthService클래스에서 Member클래스로 받은 회원정보를 AuthInfo에 저장하고, LoginController에서 Service클래스의 메서드를 사용해서 로그인 성공 혹은 실패 페이지로 이동하게 한다.

다음 할 작업은 컨트롤러와 서비스를 스프링 빈으로 등록하는 것이다.

3. 컨트롤러에서 HttpSession사용

로그인 상태를 유지하기 위해선 Httpsession을 사용하거나 쿠키를 사용하는 방식을 사용한다.

컨트롤러에서 httpSession을 사용하려면 요청매핑 어노테이션 적용 메서드에 Httpsession 파라미터를 추가한다.
요청 매핑 어노테이션에 HttpServletRequest 파라미터를 추가하고 HttpServletRquest를 이용해서 HttpSession을 구한다. 

