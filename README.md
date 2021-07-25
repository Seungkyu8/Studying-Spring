# Spring 공부 메모장

Gradle로 프로젝트 생성 - Gradle 이 버젼설정하고 라이브러리 가져오는 정도로 이해하기.

src 에 main과 test가 있음.

java파일 제외한 나머지는 다 resources 로 보면 됨.

정적 컨텐츠란?
파일을 그대로 웹브라우저에 출력하는 것. 따로 프로그래밍은 안됨.

MVC와 템플릿 엔진
템플릿 엔진을 MVC 방식으로 쪼개서 뷰를 HTML을 렌더링한 것을 클라이언트에게 전달해줌.
서버에서 ex. HTML을 조금 변경해서 출력하는 동적인것.
(Model, View, Controller)

API방식 : JSON이라는 데이터 구조 포맷으로 클라이언트에게 데이터를 전달하는 방식. (객체 전달)
(뷰, 리액트, 서버)

테스트는 순서에 의존해서 설계하면 안됨. 순서는 항상 따로 동작하게 설계할 것. 순서는 
임의적으로 선정되어 동작함. 그러기 위해선 하나의 테스트가 끝나고 나서는 저장소나
공용 데이터들을 .clear()로 지워줘야 됨.

틀을 만들어 놓고 작품을 하는것. 테스트주도개발 = TDD
.ifPresent(A) 는 NULL이 아닌 A값이 있으면 실행되는 명령어 (Optional이기 때문에 사용가능)
NULL일 가능성이 있는 경우 Optional을 한번 감쌓아서 사용한다.

throw new IllegalStateException(): 은?
부정한 인수, 또는 부적절한 인수를 메서드에 건네준 것을 나타내기 위해서 발생되며, 해당 문구를
출력해준다.


테스트검증 시, Assertions(junit말고 assertj)를 사용하여 검증.
.isEqualTo = 서로 같은지 확인.
aasetThat(검사할 대상데이터).isEqualTo(매치할 데이터) 이런 구조로 사용.

assertThrows() = 반환이 가능함으로 변수로 받는것이 가능하다.
만약 memberService.join(member1);이 실행된 후에 
assertThrows(IlleagalStateException.class, () -> memberService.join(member2));을 입력하면
미리 설정해둔 IllegalStateException("이미 존재하는 회원입니다."); 가 불려지기 전에 람다식으로
쓰여진 ->인 memberService.join(member2)가 실행되고 난 후 실행된다.
Long타입을 입력 시, L을 붙여줘야함. ex Long 타입 1을 입력 시, 1L로 입력해야 함.

스프링 기반으로 바꿀 경우 AppConfig에 @Configuration 애노테이션을 붙인다. 그 후 모든 메서드에
@Bean (스프링 빈)을 붙여준다. 그럼 스프링 컨테이너에 등록이 된다.

스프링 생성
모든 스프링은 ApplicationContext로 시작한다. 그 자체로 스프링 컨테이너라고 봐도 된다.
생성하는 건 AnnotationConfigApplicationContext()하고 ()안에 파라미터로는 스프링컨테이너가 있는
클래스 (ex. AppConfig.class)를 넣는다.
가져오는 건 getBean(이름과 그 이름.class) 형식으로 가져온다.
메서드 이름을 바꿀 수 있다.
@Bean(name="mmm") 이런식으로 가능

