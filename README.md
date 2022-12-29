# Study Modern C++:open_book:
## Table of Contents:label:
* [Study Plan](#study-planstar2) 
* [1주차](#1주차-221030star)
* [2주차](#2주차-221105star)
* [3주차](#3주차-221120star)
* [4주차](#4주차-221222star)
* [5주차](#5주차-221229star)
---
## Study Plan:star2:
- [필요한 것만 골라 배우는 모던 C++](http://www.yes24.com/product/goods/114873221)
- [씹어먹는 C++](https://modoocode.com/135)
- ~~챕터 1개당 1 or 2주 간 읽어온 후, 스터디 시간에 간단히 리뷰 및 연습 문제 풀이~~ 프로젝트 기반으로 진행
- ~~진행 시간은 일요일 오전 8시~~ 진행 시간은 목요일 오후 8시
- 일정이 불가능하거나, 변동이 필요한 경우, 카톡방에 내용 공유
- 진행에 따라 내용을 업데이트 예정
---
### 1주차 (22/10/30):star:
- 전체 진행 일정 조정
  - 2주차 리뷰 예정 내용
    - 1장 C++ 기초
    - 2장 클래스
---
### 2주차 (22/11/05):star:
- 1장 C++ 기초
  - 1.1 생애 첫 C++ 프로그램
    - `namespace std`를 꼭 쓸 필요는 없지만, 써 주는 것이 다른 사람이 코드를 볼 때 이해가 쉽다.
    - 입, 출력 기능은 C++의 핵심 언어의 일부가 아님 (명시적으로 `iostream`을 `include` 시켜줘야한다)
    - 모든 C++ 프로그램은 `main` 함수의 호출로 시작되며, `return`으로 하나의 정수를 돌려주는데 0은 정상 종료를 의미한다.
    - 중괄호({})는 여러 코드 문장을 하나의 코드 블록으로 묶는 역할을 한다. (복합문)
    - `std::`는 그 다음에 나오는 이름이 표준 `namespace`에 포함된다는 뜻 (`namespace`는 이름을 관리하는 수단)
    - 문자열 상수(문자열 리터럴)은 큰따옴표("")로 감싼다. ('a' != "a")
    - **프로그래밍 언어를 배우는 유일한 길은 실제로 사용해 보는 것이다.**
  - 1.2 변수
    - C++은 강 형식 언어(strongly typed language)
    - 변수는 형식 이름 다음에 변수 이름이 오는 형태의 문장으로 선언
    - 변수 이름 다음에 변수의 초기화 구문을 둘 수 있으며, 쉼표를 이용해서 변수 이름을 여러 개 나열할 수도 있다.
    - 각 내장 형식들은 컴파일러 별로 사용하는 메모리 공간의 크기가 다르다. (컴파일러에 상관 없이 같고 싶다면, `int8_t`, `uint16_t` 등을 쓰자)
    - 'a' + 7 = 'h'가 되지만, 읽는 사람이 화가날 수 있으므로 절대 쓰지 말자.
    - 문자열을 다룰 때는 <string> 헤더를 추가하자.
    - <C++14> 문자열 리터럴을 string으로 취급하려면 접미사 s를 붙여야한다. ("Hello" --> char [], "Hello"s --> string)
    - 변수는 최대한 늦게 선언해라. 보통 처음 사용하기 직전에 선언하는 것이 좋다, 변수를 초기화할 수 있는 지점 이후여야만 한다.
    - 상수 변수는 선언과 동시에 초기화 되어야하며, 변수가 사용되는 곳 어디든 사용이 가능하다.
    - 리터럴 값에 붙는 접미사에 따라, 형식이 지정된다. (u, l, f, ul, l 등)
    - <C++14> 숫자들 사이에 가독성을 위해 어포스트로피를 삽입 가능 (')
    - 중괄호로 초기화를 사용하면, narrowing conversion을 허용하지 않음 (컴파일 오류 발생)
    - 좁아지는 오류가 양방향으로 발생할 수도 있다.
    - 전역 변수는 사용하지 말라. (전역 `상수` 변수는 허용)
    - 지역 변수는 {} 블록에 한정됨. (C++은 `GC`가 없음 --> {}를 탈출하면 안에서 정의한 변수들 다 사라짐)
  - 1.3 연산자
    - 연산자는 사용자 정의 형식에 대해 중복적재(`overloading`)할 수 있다.(`overloading` --> 함수 이름은 같으나, 입력 인수에 따라 다른 함수가 호출되는 것)
    - 연산자의 우선순위가 분명 존재하지만, 아무도 모름 (그냥 괄호를 잘 치는 것이 좋다)
    - 전위 증가는 먼저 증가 후 `return`, 후위 증가는 `return` 후 증가
    - 주소 지정이 가능한 데이터 항목을 C++에서는 `lvalue`라고 지칭
    - 산술 표현식에서는 증가, 감소 연산자 대신 j+1처럼 명시적으로 더하거나 빼주는 것이 좋다.
    - 표현식 안에서 값을 수정하는 것은 위험하다, 수정을 개별적으로 수행하자.
    - 이항 연산의 인수들의 형식이 다르면, 둘 중 하나 또는 둘 다가 공통의 형식으로 변환된다. (그냥 수동으로 형변환 해주는게 편할 때가 많다)
    - 삼중비교 (`<=>`) a.k.a. 우주선 연산자 (ufo 연산자), a <=> b --> a < b인 경우 -1, a == b면 0, a > b면 1이 나옴
      - 그치만 그냥 a > b, a == b, a < b를 쓰자.
    - C++도 not이 있다. (not false --> true)
    - 논리 표현식에는 꼭 `bool`을 쓰자.
    - 등호 양변의 형식이 다르면 우변이 좌변의 형식으로 변환된다. (float a = 1.0으로 적으면, 1.0이 float으로 변환된다.)
    - 소프트웨어 설계의 주요 원칙 중 하나는 `관심사의 분리` (유연성이 증가하고, 복잡성이 감소한다.)
    - 함수형 프로그래밍 스타일로 작성하면 은근 유리하다. (배정문에서 변경되는 것은 배정 연산자의 왼쪽에 있는 변수뿐이어야 한다.)
    - 사람이 이해하기 쉬운 코드일 수록, 컴파일러가 최적화하기도 쉽다.
  - 1.4 표현식과 문장
    - `if`문의 각 갈래는 각자 하나의 범위를 형성한다.
    - 중괄호를 쓰는 것이 바람직하다. (한줄만 수행을 하더라도)
    - 가독성을 위해서 중괄호 안의 문장을 들여쓰자.
    - <C++17> 조건식에서 변수 선언 가능
    - <C++17> `switch-case` 문에서 [[fallthrough]]가 추가됨 (아래로 흘러가도록 설정 가능)
    - `while`은 선 조건 검사 후 실행, `do-while`은 선 실행 후 조건 검사 (`do-while`은 최소 1회는 실행된다)
    - `for`문은 초기화 절, 조건식, 단계 연산으로 사용 가능
    - 내장 형식에서는 ++i나 i++나 별로 차이가 없지만, 사용자 정의 형식에서는 i++를 사용하면 쓸데없는 복사 연산이 되므로, ++i를 권장
    - 초기화 절에는 모든 종류의 표현식과 변수 선언이 가능, 비워두기도 가능, 같은 형식의 변수 여러 개를 선언하는 것도 가능
    - 루프 색인을 루프 본문에서 수정하는 것도 가능하지만, 당연히 하지 않은 것을 권장
    - <C++11> 구간 기반 `for` 루프 ( `for` (int i : 배열)과 같은 식으로 입력하면 배열 내부의 값이 i에 순차적으로 들어간다. )
    - <C++20> 구간 기반 루프의 시작 지점에 초기화도 가능하다.
    - `goto`는 절대 쓰지 말 것
  - 다음주 계획
    - 1장 마무리 및 1장 연습문제 풀이
---
### 3주차 (22/11/20):star:
- 1장 C++ 기초
  - 1.5 함수
    - 값 전달, 참조 전달 두 가지 방식
    - 값 전달은 변수를 복사해서 사용! (실제 값에는 영향 없음)
    - 참조 전달은 변수를 직접 사용! (실제 값에도 영향 있음)
    - 함수에도 기본 인수 값을 설정할 수 있음
    - 표현식 템플릿은 주어진 계산을 그 결과가 실제로 저장되는 시점까지 미룸으로써 불필요한 복사를 방지한다 (?????, TODO.)
    - 함수 호출은 사실 공짜가 아님 (이를 공짜로 만들어주는 것이 인라인화)
    - `함수 이름`, `매개변수 개수`, `매개변수 형식`이 함수의 서명이며, 이 값이 함수 오버로딩을 구분하는 기준값이 된다.
    - main함수에는 `argc`, `argv`의 2가지 인수를 받을 수 있다.
  - 1.6 오류 처리
    - `assertion`은 프로그래머의 실수를 검출하기 위함이며, 해당 구문이 `false`이면 코드가 종료
    - `assertion`의 장점 중 하나는 `Release` 모드로 빌드 시, 동작하지 않는다는 것
    - 일반적인 오류 처리는 `try`, `catch` 구문을 활용할 수 있음
    - 오류가 발생할 수 있는 곳에서 `try`
    - 오류가 발생하면 동작할 부분을 `catch` 사용
    - `catch`는 다중으로 사용 가능하며, 입력되는 값이나, 예외 종류에 따라 다르게 동작하도록 할 수 있음
    - 예외가 발생해도 그냥 무시하고 진행하고 싶다면 빈 `catch`를 추가한다.
    - `static_assert`는 컴파일 시점에서 오류를 검출하기 위함
  - 1.7 파일 입출력
    - 파일 입출력 및 파일 시스템 관련 입출력이 존재
    - 필요한 상황에 맞춰서 구글 검색을 잘 해서 사용하면 될 것으로 보임
  - 1.8 배열, 포인터, 참조
    - 배열은 선언 시에 크기를 지정해줘야함 (싫을 경우, 동적할당)
    - 배열 접근 시, 색인의 유효성이 점검되지 않는다. (C++ Array로 해결 가능)
    - 동적 할당 시에 포인터의 `new`, `delete`를 같이 사용해줘야 한다.
    - 꼭 메모리 할당과 해제를 해줘야만 메모리 누수를 방지할 수 있음
    - 포인터는 `메모리 주소`를 저장하는 변수를 의미
    - 포인터의 초기화는 `nullptr` (C++ 11이상)
    - 포인터는 결국 메모리를 직접 사용하는 것이므로, 잘 사용하지 않으면, 여러 방면으로 오작동할 수 있음
    - 이를 해결하기 위해서는 라이브러리 내부의 컨테이너, RAII를 이용한 캡슐화, 스마트 포인터 등을 사용하면 좋다.
    - `unique_ptr`은 객체에 대한 유일한 소유권을 나타내는 포인터 (동일한 객체에 대해 여러 개 생성 불가)
    - `shared_ptr`은 공유 포인터를 의미하며, 일반적인 포인터처럼 사용이 가능, 순환 참조 문제 발생 시 위험할 수 있으며, `make_shared`를 이용해서 생성하는 것이 안정적이고 좋다.
    - 참조는 해당 변수에 대한 별명을 생성하는 것
    - 함수에서 참조를 Return할 때는 주의할 것 (상한 참조)
    - `vector`는 `Python`의 `list`와 유사한 컨테이너
    - `valarray`는 성분별 연산을 지원함, 쓰는걸 본적은 없음
  - 1.9 소프트웨어 프로젝트의 구조화
    - 주석 작성 시, 중첩된 주석 안되므로 주의
    - 매크로는 되도록 피하고, 상수, inline, constexpr 등을 활용할 것
    - 포함가드를 이용하면, 헤더 파일 중복 정의를 피할 수 있으며, `#pragma once`에 비해 이식성이 좋게 사용할 수 있다.
    - 조건부 컴파일을 이용하면, 디버깅 상황에 특별한 로깅을 수행하도록 할 수 있으며, `Window`, `Linux & Unix`에 맞춰서 코드를 추가할 수 있도록 할 수 있으며, 라이브러리 존재 유무를 이용하여, 코드를 다양하게 작성할 수 있다.
    - 또한, C++의 새로운 기능이 추가되었는 지 여부에 따라, 코드를 사용할 수 있다.
---
### 4주차 (22/12/22):star:
- 진행 방식 변경
  - 스터디 시간 변경 $\rightarrow$ 목요일 오후 8시
  - 스터디 방식 변경 $\rightarrow$ 프로젝트 위주 코드 작성
  - 스터디 참고 문서 추가 $\rightarrow$ [씹어먹는 C++](https://modoocode.com/135)
  - 다음주까지 개인별로 프로젝트 주제 정해오기
---
### 5주차 (22/12/29):star:
- 주제 선정
  - 재훈 : `SLAM`을 간단히 만들어볼 예정 (시작은 `ICP` 부터 진행, `ROS` 사용 예정)
  - 예빈 : 테트리스 (Visual Studio 사용 예정 --> `MSVC`)
  - 범훈 : 일단 패스
  - 동현 : 시뮬레이터 제작 (프로그램 미정)
  - 준규 : 쉐이더를 이용해서 디펜스 게임
  - 우성 : 실제 드론 제어
- 매주 코드 리뷰를 진행 
- 새롭게 알게된 내용을 공유
---