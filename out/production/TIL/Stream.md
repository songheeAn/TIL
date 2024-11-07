# 😊 오늘 공부한 내용

## 스트림(Stream)이란?
- 다양한 데이터 소스를 표준화된 방법으로 다루기 위한 개념
- 컬렉션, 배열 등을 스트림으로 변환하여 데이터의 연속적인 흐름으로 처리
- 데이터 소스로부터 데이터를 읽기만 할 뿐, 변경하지 않음
- 스트림은 내부 반복으로 작업을 처리
- 기본 순서
    1. **스트림 생성**
    2. **중간 연산** (0~n번 가능)
    3. **최종 연산** (0~1번 가능)

## 기본형 스트림 (IntStream, LongStream, DoubleStream)
- 오토박싱과 언박싱의 비효율성을 제거
- 숫자 관련 유용한 메서드를 제공
    - 예시: `IntStream`의 `count()`, `sum()`, `average()` 등

---

## 스트림 생성 방법

- **컬렉션으로부터 스트림 생성**
    ```java
    List<Integer> list = Arrays.asList(1, 2, 3);
    Stream<Integer> intStream = list.stream();
    ```
- **배열로부터 스트림 생성**
    ```java
    Stream<String> strStream = Stream.of("a", "b", "c");
    Stream<String> strStream = Stream.of(new String[] {"a", "b", "c"});
    Stream<String> strStream = Arrays.stream(new String[] {"a", "b", "c"});
    Stream<String> strStream = Arrays.stream(new String[] {"a", "b", "c"}, 0, 3);
    ```

---

## 스트림의 연산 - 중간 연산

| 중간 연산                               | 설명                           |
| --------------------------------------- | ------------------------------ |
| `Stream<T> filter()`                    | 조건에 맞지 않는 요소 제거      |
| `Stream<T> distinct()`                  | 중복 제거                       |
| `Stream<T> skip(long n)`                | 스트림 일부 건너뜀              |
| `Stream<T> limit(long maxSize)`         | 스트림 일부 잘라내기            |
| `Stream<T> sorted()`                    | 스트림 기본 정렬                |
| `Stream<T> sorted(Comparator<T> comparator)` | 스트림 정렬 기준에 맞춰 정렬   |
| `map(Function<T, R> mapper)`            | 스트림의 요소 변환              |
| `flatMap(Function<T, R> mapper)`        | 스트림의 스트림을 스트림으로 변환 |
| `mapToInt()`, `mapToLong()`, `mapToDouble()` | 스트림을 기본형 스트림으로 변환 |
---
## 😌 느낀점
- 개념적으로는 이해했지만, 실제 문제를 풀 때 개념을 어떻게 적용해야 할지 더 연습할 필요성을 느꼈다. 특히 스트림의 중간 연산을 다양한 상황에서 유연하게 활용하는 연습이 필요하다고 생각했다. 앞으로 여러 예제 문제를 통해 개념을 실전에 맞게 적용할 수 있도록 연습해보고 싶다.