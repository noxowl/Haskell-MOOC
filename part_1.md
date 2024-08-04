# Haskell MOOC - Part 1

## Haskell 기본
- Haskell의 특징
    - 부작용 없는 순수 함수
    - 무한을 다룰 수 있는 지연 평가
    - 강력한 타입 시스템
    - 타입 어노테이션을 통한 타입 추론
    - 가비지 콜렉션
    - 컴파일 언어
- Haskell의 주요 기능
    - 고차 함수: 함수의 인수로 함수를 줄 수 있다.
        - <code>map length ["abc", "defg"]</code> -> <code>[3, 4]</code>
    - 람다
    - 부분적용(여러 인자를 받는 함수의 일부 인자를 고정하고 다음 호출 시 결과를 반환한다. <-> 커링: 하나씩만 고정. 모든 인자를 만족할 때까지 지속적으로 함수를 생성하므로 매 호출에서 인자 1개씩을 고정하는 연속적 부분적용으로 볼 수 있다.)
    - 대수적 데이터 타입 정의
    - 패턴 매칭
    - 빌트인 리스트 구문 (CafeOBJ처럼 직접 안 만들어도 된다) 및 지연 평가를 통한 무한 리스트
    - 파라미터화 된 타입
    - 타입 클래스를 통한 다형성
- Haskell의 모든 것은 Expression과 Type이다.
    - Expression은 괄호로 그룹화 할 수 있다.
    - Haskell의 Expression 평가는 Leftmost-Outermost이므로 이로 인해 무한 리스트를 다룰 수 있게 된다.
- 기본 타입
    - Haskell의 타입 이름은 대문자로 시작한다. Boolean을 제외한 모든 변수와 함수는 소문자로 시작한다.
    - 함수 유형은 -> 로 작성한다.
        - argumentType -> returnType
        - 두 개 이상의 인수는 공백이 아니라 -> 를 또 넣는다.
        - arg1 -> arg2 -> return
    - Int: 1, 2, -3. Number (Signed 64bit), operators: div (정수 나눗셈)
    - Integer: 1, -2,900000000000000000. Unbounded number
    - Double: 0.1, 1.2e5. Floating point numbers. operators: \/ (일반 나눗셈)
    - Bool: True, False. Boolean
    - String: "abcd", "". aka [Char]. operators: reverse, ++

## Haskell 기본 - 001
- 조건문
    - <code>x = if y == z then 1 else 2</code>
    - 값을 반환해야만 하므로 else는 생략될 수 없다.
    - 비교연산에서 <code>!=</code> 대신 <code>/=</code> 를 사용한다.
- Local Definitions
    - <code>let ... in</code> 구문과 <code>where</code> 구문으로 로컬 정의를 할 수 있다.
    - <code>circleArea r = let pi = 3.1415926 \n rsquare = r * r \n in pi * rsquare</code>
    - <code>circleArea r = pi * square r \n where pi = 3.1415926 \n square x = x * x</code>
    - Haskell의 변수는 기본 불변하다. (CafeOBJ 수업에서 말한 것과 동일)
        - 그러므로 아래와 같은 코드는 평가되지 않는다.
        - <code>increment x = let x = x+1 \n in x</code>
    - 스코프 한정적으로 작동하는 섀도잉은 존재한다.
- Pattern Matching
     - _ 로 와일드카드를 둘 수 있다. (위에서 아래로 평가되므로 마지막에 둬야 함)
     - <code>greet :: String -> String -> String</code>
     - <code>greet "Korea" name = "Annyong, " ++ name</code>
     - <code>greet "Japan" name = "Otsukaresama, " ++ name</code>
     - <code>greet _ name = "Hello, " ++ name</code>
- 재귀
    - 루프를 위해 재귀를 사용하며 Haskell이 알아서 최적화 한다.
- 들여쓰기
    - Python과 비슷하게 들여쓰기가 구분 분석에서 중요하다.

## Haskell 기본 - 002
- 재귀 및 헬퍼 함수 (꼬리 재귀)
- Guard
    - 입력에 대한 조건을 제한할 수 있다.
- 리스트
    - Haskell의 함수 순수성으로 인해 리스트 연산은 입력된 리스트를 변형하지 않고 새 리스트를 반환한다.
- 유형 추론 및 다형성
- Maybe
    - null 대신 값이 없음을 안전하게 표현하고 패턴매칭으로 간결하게 처리할 수 있다.
- Either
    - 관례적으로 Right가 correct, Left는 error 이다. (Rust의 Result monad)
