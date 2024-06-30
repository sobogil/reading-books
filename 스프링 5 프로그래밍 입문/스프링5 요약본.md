*챕터 11 296페이지부터 작성을 시작하여 이전 내용이 없는 것은 양해를 부탁드립니다.

## 📝 목차
- [Chapter11](#Chapter11)

##Chapter11 MVC 1: 요청 매핑, 커맨드 객체, 리다이렉트, 폼 태그, 모델

12. 커맨드객체: 중첩•콜렉션 프로퍼티

기존의 커맨드 객체로 사용한 클래스와 달리 중접(클래스 내에서 사용한 프로퍼티가 다시 다른 프로퍼티로 표현이 됨)프로퍼티를 갖고 리스트 타입의 프로퍼티를 AnsweredData클래스가 갖는다. 

중첩 프로퍼티나 리스트 타입의 프로퍼티를 갖더라도 http요청 파라미터 이름에 인덱스를 붙여 리스트를 표현하거나 프로퍼티이름.프로퍼티이름(처음은 소문자)로 표현하면 된다.

13.model을 통해 컨트롤러에서 뷰에 데이터 전달

model 파라미터를 만들어 addAttribute()로 뷰에서 사용할 데이터를 전달한다.
jsp 같은 경우 ${}을 통해 표현할 수 있다.

데이터 베이스에서 데이터를 가져오면 컨트롤러에서 데이터를 model객체를 만들어 뷰로 넘기는 과정이 진행된다.

13.1 ModelAndView를 통한 뷰 선택

ModelAndView 타입을 이용해서 뷰에 전달할 모델 데이터는 addObject()로 추가 
뷰이름은 setViewName()으로 지정

13.2 get,set방식에 동일 이름 커맨드 객체 사용가능중

커맨드 객체를 파라미터로 추가가 가능하며 포스트 겟 방식을 구분할때 @ModelAttribute어노테이션을 사용하면 좋다.

14.주요 폼 태그

<form:form>
<input>관련 태그 : <form:input>, <form:password>, <form:hidden> 연결할 커맨드 객체의 프로퍼티를 path속성으로 설정한다.

<select>관련 태그 : <form:select>, <form:options>, <form:option>

체크박스 관련 태그 : <form:checkboxes>, <form:checkbox>

radio버튼 관련 태그 : <form:radiobuttons>, <form:radiobutton>

textarea 태그를 위한 태그 : <form:textarea>
