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