## 📝 목차
- [Chapter12](#Chapter12)

##Chapter12 MVC 2: 메시지, 커맨드 객체 검증

2. <spring:message> 태그 사용하기

문자열을 별도의 파일로 저장하고 jsp코드에서 메시지 값을 가져올 때 사용한다.
MessageSource빈을 설정하고 jsp에서 스피링메시지 태그를 사용해 메시지를 가져온다.

<label>이메일</label>이런식으로 저장해두면 나중에 나라마다 언어가 다르거나 해당 메시지를 바꾸고 싶을 때 모든 파일을 전부다 고쳐야하므로 스프링 메시지 태그를 사용한다.

프로퍼티에 저장해서 사용하는 방식
예)
name=이름
email=이메일
password=비밀번호
password.confirm=비밀번호 확인

2.1 messagesource와 스프링 메시지 태그

스프링은 메시지를 관리할 수 있는 MessageSource인터페이스를 정의하고 있다.
getMessage()를 통해 필요한 메시지를 가져와서 사용하는 식이다.


3. 커맨드 객체의 값 검증과 에러 메시지 처리

가입에 실패한 이유를 알려줘야 하고 올바르지 않은 값을 입력했을 때 동작하지 않도록 해줘야 한다. 즉 폼 검증과 에러 메시지 처리는 아주 중요한 문제이다. 

스프링은 이 두문제를 다음과 같은 방법을 제시한다.
-커맨드 객체를 검증하고 결과를 에러코드로 저장
-jsp에서 에러 코드로부터 메시지를 출력

3.1 커맨드 객체 검증과 에러 코드 지정

객체를 검증할 때는 Validator인터페이스를 사용한다. supports()메서드는 검증할수 있는 타입인지 확인하고 validate()메서드가 첫 번째 파라미터로 받은 객체를 검증하고 오류 결과를 Errors에 담는다.

ValidationUtils.rejectIfEmptyOrWhitespace()메서드는 target을 파라미터로 받지 않아도 target 객체의 특정 프로퍼티에 접근할 수 있는데 이 이유로는 스프링 MVC에서 Validator를 사용하는 코드는 요청 매핑 애노테이션을 적용하는 메서드에서 Errors타입의 파라미터를 전달받으므로 Errors객채에 있는 getFieldValue() 메서드를 통해 특정 프로퍼티의 값을 구할 수 있다.

특정 프로퍼티에 에러가 생기면 rejectValue()사용 커맨드 객체가 문제가 생기면(로그인 폼에서 아이디 비밀번호가 둘다 에러가 생겼을 때)는 reject()로 에러를 추가한다.

3.3 커맨드 객체의 에러 메시지 출력

스프링에서 제공하는 <form:errors>태그를 이용하면 출력할 수 있다.
ex)<form:errors path="email">

4. 글로벌 범위 Validator 컨트롤러 범위 Validator    

모든 컨트롤러에 적용가능한 글로벌 validator와 단일 컨트롤러에 적용 가능한 validator를 설정할 수 있다. @valid 어노테이션을 사용해 커맨드 객체에 검증 기능 적용 가능.

4.1 글로벌 벙위 validator설정과 @valid어노테이션

설정클래스에서 WebMvcConfigurer 의 getValidator()메서드가 Validator구현 객체를 리턴하도록 구현, 글로벌 범위 validator가 검증할 커맨드 객체에 @valid어노테이션 적용

즉 getValidator()가 리턴한 값을 글로벌 범위 validator로 사용

validator 클래스를 만든 다음 해당 객체를 getValidator()로 리턴하면 글로벌 validator가 되어 컨트롤러에서 커맨드 객체 앞에 @Valid 어노테이션을 붙여서 글로벌 범위로 적용할 수 있다.

글로벌 validator를 이용하면 검증 코드를 새로 짤 필요 없이 error를 이용해 검증하면 된다. 단 Errors타입 파라미터가 없으면 400에러가 뜬다.

스플링 MVC에서는 자체적으로 제공하는 Validator가 존재한다. 

4.2 @initBinder 어노테이션을 이용한 컨트롤러 범위 validator

@initBinder로 컨트롤러 범위 validator를 설정할 수 있다.

@Valid는 동일하게 사용하되 컨트롤러 클래스에 @initBinder어노테이션이 적용되는 메서드를 만들고 WebDataBinder 파라미터의 setValidator()메서드로 Validator를 적용시켜주면 된다.

5. Bean Validation 사용

bean validation관련 의존을 추가해 @NotBlank, @Email, @NotEmpty등의 어노테이션을 추가해서 커맨드 객체를 검증할 수 있다.

OptionalValidatorFactoryBean을 빈에 등록해야하며 @EnableWebMvc를 설정했다면 추가로 설정할 것은 없다.
