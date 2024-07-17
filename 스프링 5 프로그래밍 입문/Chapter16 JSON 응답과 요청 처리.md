## 📝 목차
- [Chapter16](#Chapter16)

## Chapter16 JSON 응답과 요청 처리

3. @RestController로 JSON 형식 응답

@Controller 대신 @RestController를 사용하면 Json형식으로 응답을 할 수 있다.

3.1 @JsonIgnore를 이용한 제외 처리

password같은 민감한 정보를 제외하고 json형태로 보내고 싶을때 @JsonIgnore을 이용하면 된다.

3.2 날짜 형식 변환 처리: @JsonFormat

@JsonFormat을 이용해서 날짜 처리를 한다.

4. @RequestBody로 Json 요청 처리

@RequestBody를 커맨드 객체에 붙이면 JSON 형식의 문자열을 해당 자바 객체로 변환한다.

5. ResponseEntity로 객체 리턴하고 응답 코드 지정하기

지금까지는 상태코드를 지정하기 위해 HttpServletResponse의 setStatus()와 sendError()를 사용했다. 이렇게 했을 경우 404응답을 json형태가 아닌 서버가 기본으로 제공하는 Html을 응답 결과로 제공한다는 점이다. 
API를 호출하는 프로그램 입장에서 JSON 응답과 HTML응답을 모두 처리하는 것은 부담스럽다.

5.1 ResponseEntity를 이용한 응답 데이터 처리

ResponseEntity를 생성하는 기본 방법은 status와 body를 이용해서 상태 코드와 json으로 변환할 객체를 지정하는 것이다.
