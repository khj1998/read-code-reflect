# 2장 리팩터링 원칙

## 2.1 리팩터링 정의 🤓

- 리팩터링은 동사이면서 명사
- `함수 추출하기`, `조건부 로직을 다형성으로 바꾸기` 등 기법을 의미하기도 함
- **항상 정상 작동**하기 때문에 언제든 멈출 수 있어야함

```text

?? : 리팩터링하다가 코드가 깨져서 며칠동안 수정함;;;

마틴 파울러 : ???

```

## 2.2 두개의 모자 🎩

- 개발자가 개발하는 모드는 크게 두가지
    1. 기능 추가
    2. 리팩터링
- 부디 하나에만 집중하자

?? : 5252 인간은 멀티캐스팅이 불가능하다구?

- 주니어 개발자에서 주는 일침으로 들림 마치 like `Context Switching`
- 지금 하는것에 집중하세요.

## 2.3 리팩터링하는 이유 🦷

요약 ) 리팩터링하면 유익이 크단다를 귀납적으로 증명해줌. 설계, 가독성, 버그 찾기, 프로그래밍 생산성 등 다양한 방면에서 유익이다. ((근데 왜 안함?))

## 2.4 언제 리팩터링? 🧐

**준비를 위한 리팩터링**

리팩터링하기 가장 좋은 시점은 기능을 새로 추가할때. 추후 기능 개발을 위해 `함수 매개변수화하기` 적용 요망

**이해를 위한 리팩터링**

이해가 잘안된다? 리팩토링 해야할때

**쓰레기 줍기 리팩터링**

**계획된 리팩터링과 수시로 하는 리팩터링**

**오래 걸리는 리팩터링**

**코드 리뷰에 리팩터링 활용하기 (페어 프로그래밍)**

**관리자에게는?**

“리팩토링한다고 말하지 말라”(가능하려나…)

**리팩토링 하지 말아야할때**

외부 api 호출할때, 처음부터 작성하는게 쉬울때 it’s up to you …

## 2.5 리팩터링 시 고려할 문제 👿

나는 누가 특정한 기술, 도구, 아키텍처 등을 내세울 때마다 항상 문제점을 찾는다. **(Trade-off 를 항상 계산한다는 말. 배우려고 하는 자세, 자신이 틀릴 수도 있다는 자세)**

난 리팩토링이 많은 팀에서 적극적으로 도입해야 할 중요한 기법이라고 믿지만 리팩토링이 딸려오는 문제점도 엄연히 있다.

이런 문제가 언제 발생하고 어떻게 대처해야 하는지 반드시 알고 있어야 한다.

**새 기능 개발 속도 저하**

많은 사람들이 리팩토링 떄문에 새 기능 개발하는 속도가 느려진다고 생각한다.

하지만 리팩토링의 궁극적인 목적은 개발 속도를 높이는 데 있다.

**리팩토링의 궁극적인 목표는 개발 속도를 높여서, 더 적은 노력으로 더 많은 가치를 창출하는 것이다.**

리팩토링이 필요해 보이지만 추가하려는 기능이 아주 작아서 기능 추가부터 하고 싶은 상황에 마주할 수도 있다.

이 경우라도 준비를 위한 리팩토링을 하면 변경을 훨씬 쉽게 할 수 있다.

그래서 새 기능을 구현해넣기 편해지겠다 싶은 리팩토링이라면 주저하지 말고 리팩토링부터 한다.

내가 직접 건드릴 일이 거의 없거나 불편한 정도가 그리 심하지 않는다고 판단되면 리팩토링 하지 않는 편이다.

여기서 주의할 점은 리팩토링을 "클린 코드" 를 위해 너무 집착하는 것이다. **(확실히 클린 코드를 너무 신경쓰다 보면 생산성이 떨어지는 것 같다.)**

리팩토링의 본질을 잊지말자. 리팩토링은 `개발 기간을 단축하고자` 하는 것이다.

리팩토링의 동력은 경제적인 효과를 늘 생각하자.

**코드 소유권**

외부 라이브러리 사용 혹은 이미 제공된 API의 경우 수정이 까다로울 수 있다. 그 함수에서 다른 함수를 호출하도록 우회하여 소유권을 가져오기 ㅋ

**브랜치**

지속적 통합, 익스트림 프로그래밍을 통하여 리팩토링을 할 수 있는 환경 가꾸기

**테스팅**

누누히 말하지만 자가 테스트 코드(JUnit 등)이 중요

**레거시 코드**

물려받기 싫은게 코드 222222

테스트 코드도 사실 적합한 코드가 있다. 그래서 테스트 코드를 추가하기 쉽지 않을 수 있다. 새로운 기능부터 차근차근 적용해보길

**데이터베이스**

1. 새 필드 선언 (사용 X)
2. 기존 필드, 새 필드 모두 사용
3. 읽을때는 새 필드만 읽게
4. 예전 필드 삭제

이처럼 점진적인 리팩토링 요망

## 2.6 리팩터링, 아키텍처 그리고 애그니

요구사항을 사전에 모두 파악해두는것은 사실상 불가능

그러므로 아키텍처도 변화해야함 → 리팩터링

YAGNI → 기존 코드를 폄하하는것 X. 진화하고 변화하라는 것 O.

## 2.7 리팩터링과 개발 프로세스

ㅌㄷㄷ. 익스트림 프로그래밍. 애그니. 모두 리팩터링의 원인이자 결과. 충분히 연습하고 체화할것.

## 2.8 리팩터링과 성능 **⚙️**

**직관적인 설계 vs 성능**

1. 튜닝하기 쉽게 만들어두기
2. 튜닝하기

1번을 다른 말로 하면 **리팩터링**

서비스의 특징을 명확하게 파악하기. 만일 하드 리얼타임(순간 포착이 중요한 시스템)에서는 컴포넌트마다 자원을 할당하고 일정 수준 이상을 넘치지 않도록 유의.

오너십을 가질것. 성능을 위해 튜닝했는데 그게 가독성을 낮춘다면 과연 꼭 필요한 성능 향상이었는지 평가할 필요가 있음.

**아무것도 안 만드는 데도 시간이 걸린단다**

의도적으로 성능 최적화를 해야하기 전까지는 가독성 혹은 수정하기 쉽게 변경하는것이 훨씬 중요 → 성능 이슈가 발생하면 오히려 높은 가독성은 빛을 발한다

## 2.9 리팩터링 유래

리팩터링이라는 워딩은 세상에 존재하지 않던거였고 지금 주류 개발 기법으로 되었다고 하네요. ㅖㅖ 그렇다고 합니다.

## 2.10 리팩터링 자동화

IDE를 적극 활용하여 리팩토링 하시오. 그리고 수동 리팩토링도 병렬적으로 하시오. 그렇다고 자동 리팩토링을 절대 신뢰하라는 것은 아닙니다. 이를 방어하기 위한 수단은 바로 테스트 코드 입니다. ㅌㄷㄷ 하세요.

## Recap

- 리팩토링의 사실과 오해 (by 마틴 파울러)
- 리팩토링은 사고방식이다.
- 읽기 쉬운 코드는 성능이 안좋다고? 너 개발을 하고 싶기는 하니? 근데 왜 네 코드는 읽기 어려워? (대충 신데렐라 언니 짤)    
- 성능 튜닝을 위한 행위 (자료구조 적용, 시간복잡도 공간복잡도 분석 등)이 모든 코드에서 필수적이진 않다
- 지금 하는것에 집중하기. 다른것들을 불안해하고 긴장하는게 아니라. 지금하고 있는것에 집중.
    - 두개의 모자. 리팩터링과 성능.
- 내가 틀릴 수도 있다. 배우려고 하고 수용적인 태도에 대한 고찰
