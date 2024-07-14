## 📝 목차
- [Chapter14](#Chapter14)

## Chapter14 MVC : 4 날짜 값 변환, @PathVariable, 익셉션 처리

3. 커맨드 객체 date 타입 프로퍼티 변환 처리: @DateTimeFormat

@DateTimeFormat 어노테이션을 이용해서 String을 localdatetime으로 변환이 가능하다.

3.1 변환에러처리

DateTimeFormat에서 패턴에 오류가 생기면 400에러가 발생하므로 요청매핑 어노테이션이 적용된 메서드에 Error파라미터를 추가하면 새로운 메시지를 볼 수 있다.

4.변환처리에 대한 이해

WebDataBinder는 커맨드 객체를 생성한다. WebDataBinder은 직접 타입을 변환하지 않고 ConversionService에 그 역할을 위임한다. @EnableWebMvc어노테이션을 사용하면 DefaultFormattingConversionService로 사용한다.

6.@PathVariable을 이용한 경로변수 처리

@PathVariable을 이용하면 중괄호에 담겨있는 경로 변수를 처리할 때 유용하다. 경로변수가 @PathVariable에 전달되어 경로 변수에 해당하는 파라미터에 적용이 된다.

7.컨트롤러 익셉션 처리하기

@ExceptionHandler어노테이션을 이용하면 컨트롤러에서 발생한 익셉션을 처리할 수 있다.

7.1 @ControllerAdvice 이용한 익셉션처리

만약 다수의 컨트롤러에서 공통된 익셉션을 처리하고 싶을때는 @ControllerAdvice어노테이션을 이용해 처리하면 된다.

