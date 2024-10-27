---
layout: default
title: 함수
parent: Kotlin
nav_order: 3
---

# Kotlin에서 함수 사용하기
{: .no_toc }

Kotlin의 다양한 함수를 학습한다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 기본 함수 선언

`fun` 키워드는 Kotlin에서 **함수 선언**에 사용된다.

- **반환 타입**을 명시할 수 있으며, 생략하면 자동으로 `Unit` 타입이 적용된다.
- **매개변수**에 `var`이나 `val` 키워드를 사용할 수 없으며, 기본적으로 **`val`이 자동으로 적용**된다.

```java
fun someFunction(data1: Int, data2: Int = 10): Int {
    return data1 + 10
    data1 = 20 // 오류: 매개변수의 값은 변경 불가
}
```


## 명명된 매개변수 사용

- 함수를 호출할 때 **매개변수의 순서를 지키지 않아도** 된다.
- 매개변수를 명명하여 전달할 수 있다.

```java
someFunction(data2 = 10, data1 = 10)
```


## 람다 함수

람다 함수는 **익명 함수**를 정의하는 방법이다.

- **`fun` 키워드와 함수 이름**을 사용하지 않는다.
- **화살표 왼쪽**은 매개변수, **오른쪽**은 함수 본문이다.
- **반환 값에 `return` 문**을 사용할 수 없다.

### 람다 함수 예제

```java
val sum = { no1: Int, no2: Int -> no1 + no2 } // 매개변수 타입 유추 가능
```

- **매개변수가 하나인 경우** `it` 키워드를 사용해 대체할 수 있다.

```java
val some: (Int) -> Unit = { println(it) }
```


## 함수 타입

함수를 **선언할 때 매개변수와 반환 타입**을 함께 나타내는 방식이다.

```java
val some: (Int, Int) -> Int = { no1: Int, no2: Int -> no1 + no2 }
```


## 고차 함수

고차 함수는 **함수를 매개변수로 전달받거나 반환**할 수 있는 함수이다.

```java
fun hofFun(arg: (Int) -> Boolean): () -> String {
    val result = if (arg(10)) {
        "valid"
    } else {
        "invalid"
    }
    return { "hofFun result: $result" }
}

val result = hofFun { no -> no > 0 }
println(result()) // hofFun result: valid
```


