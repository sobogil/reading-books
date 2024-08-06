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

repository를 사용할때 CrudRepository를 상속받아 인터페이스를 정의하면 좋다

템플릿에서 repository로 변환할때는 RedisOperations멤버 변수를 제거하고 기존의 멤버변수를 Repository멤버 변수로 교체, 다음엔 생성자 주입을 통해 RedisOperations 빈을 Repository로 교채하고 생성자 내 멤버 함수도 교체한다.


## 6.7 jpa로 repository 기반 서비스 만들기

스프링 생태계의 강점은 일관성 다른 구성에서도 동일한 접근 방식을 적용해 성공적인 결과를 얻는다.

jpa를 이용한 서비스 개발할때 먼저 도메인 클래스를 설정한다. @entity어노테이션을 적용해서 만든다음 @id, @generatedValue를 적용해서 설정
클래스 수준 어노테이션은 @RedisHash를 @Entity로 대체
필드 수준 어노테이션도 @GeneratedValue추가

다음엔 스프링 데이터의 CrudRepository를 상속하고 저장할 객체의 타입과 키를 제공해 필요한 repository인터페이스를 정의 합니다.

폴링할때 직접 생성자를 생성해 빈을 주입하는 대신 롬복 으로 생성자에 필요한 멤버 변수를 제공한다. @ReqiredArgsConstructor어노테이션과 초기화가 필요한 멤버 변수에 @NonNull어노테이션을 추가하면 롬복이 생성자 주입에 필요한 인수가 무엇인지 결정한다.

결과
로컬 컴퓨터에서 서비스를 계속 실행중인 상태에서 sbur-jap 서비스를 실행해 폴링 결과를 얻고 저장 검색하며 표시.


## 6.7.3 데이터 로드하기
스프링 부트에는 데이터 베이스를 초기화하고 채우는 매커니즘이 있다.
-DDL, DML스크립트를 사용해 초기화하고 채우기
-하이버네이트를 통해 @Entity클래스에서 테이블 구조를 자동으로 생성하고 repository빈을 통해 채우기

