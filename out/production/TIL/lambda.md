# 😊 오늘 공부한 내용

---

### 람다식이란?

- 함수(메서드)를 간단한 **식(Expression)**으로 표현하는 방법

### 함수 vs 메서드
- **함수**는 클래스에 독립적
- **메서드**는 클래스에 종속적
- 자바에서는 모든 것이 클래스 안에 있으므로 메서드 형태로 사용

---

### 람다식 작성하기

1. **메서드의 이름과 반환 타입을 제거**하고 `→`를 블록 `{}` 앞에 추가
2. 반환값이 있는 경우, **식이나 값만 적고 `return`문 생략 가능** (끝에 `;`는 붙이지 않음)
3. 매개변수의 타입이 추론 가능하면 생략 가능 (대부분의 경우 생략 가능)

---

### 람다식 작성하기 - 주의사항

1. 매개변수가 하나인 경우, 괄호 `()` 생략 가능 (타입이 없을 때만)
2. 블록 안의 문장이 하나뿐일 때, 괄호 `{}` 생략 가능 (끝에 `;`는 붙이지 않음)

---

### 실습 예제

```java
// 1번
int max(int a, int b) {
    return a > b ? a : b;
}

// 1번 - 람다식
(a, b) -> a > b ? a : b

// 2번
int printVar(String name, int i) {
    System.out.println(name + "=" + i);
}

// 2번 람다식
(name, i) -> System.out.println(name + "=" + i)

// 3번
int roll() {
    return (int)(Math.random() * 6);
}

// 3번 람다식
() -> (int)(Math.random() * 6)

```
---

## 함수형 인터페이스

- **람다식 = 익명 객체**
- 함수형 인터페이스란?
    - 단 하나의 추상 메서드만 선언된 인터페이스
    - **필요성**: 함수형 인터페이스 타입의 참조 변수로 람다식을 참조할 수 있음

### 실습 예제

```java
public class Ex1 {
    public static void main(String[] args) {
        // 람다식(익명 객체)
        // 참조변수 타입(함수형 인터페이스), 참조변수 필요
        MyFunction2 f = (a, b) -> a > b ? a : b;

        int value = f.max(3, 5);
        System.out.println(value);
    }
}

@FunctionalInterface
interface MyFunction2 {
    public abstract int max(int a, int b);
}
```
---

### 😌 느낀점
- 람다식을 공부해서 코드에서 잘 활용해보고 싶다. 이번 주도 파이팅!