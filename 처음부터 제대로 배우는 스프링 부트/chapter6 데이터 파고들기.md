도메인 두조설계 DDD를 토대로 해서 애플리케이션을 정의

@Data 롬복에서 게터,세터,이퀄스, 애쉬코드, 투스트링 메서드를 생성한다.

@NoArgsConstructor 매개변수 없는 생성자 생성

@AllArgsConstructor 각 멤버 변수의 매개변수가 있는 생성자 만든다

@JsonIgnoreProperties(ignoreUnknown = true) json 응답 필드 중에서 클래스에 상응하는 멤버 변수가 없는 경우 jackson 역 질렬화 메커니즘이 이를 무시하도록 한다.

@Id 고유 식별자를 가진다

@JsonProperty("vert_rate") 한 멤버 변수를 다른 이름이 붙은 json 필드와 연결한다.



개발자는 구현체보다 인터페이스를 기준으로 코드를 작성해야 한다.

스프링 데이터의 템플릿 지원을 이용한 데이터베이스 작업은 뛰어난 유연성을 갖춘 하위 수준 api를 제공
그러나 마찰을 최소화하고 생산성을 최대화 하며 재사용성을 찾는다면 repository지원이 더 좋은 선택

