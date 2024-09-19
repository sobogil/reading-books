# chapter5 애플리케이션 설정과 검사

@Value어노테이션은 설정을 코드에 녹이는 가장 간단한 접근방식
@Value 하나만 사용하는 속성은 IDE가 해당 속성을 애플리케이션이 사용한다고 인식을 못한다.

@ConfigurationProperties
@Value가 유연하지만 단점이 있기에 @ConfigurationProperties을 사용한다.


액추에이터는 명사로 작동시킴
액추에이터는 정의된 각 속성의 현재 값만이 아니라 해당 값이 정의된 행과 열 번호에 이르기까지 그 소스도 보여줍니다.