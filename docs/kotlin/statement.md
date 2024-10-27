---
layout: default
title: 제어문
parent: Kotlin
nav_order: 5
---

# 조건문과 반복문
{: .no_toc }

Kotlin에서 조건문과 반복문을 사용하는 방법을 학습한다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 조건문

Kotlin에서는 `if`와 `when`을 사용해 조건문을 구성하며, **표현식으로 사용**할 수 있어 유용하다.


### `if` 표현식

- `if`는 Kotlin에서 **표현식**으로 사용되며, 값을 반환할 수 있다.

```java
val result = if (data > 0) {
    println("data > 0")
    true
} else {
    println("data <= 0")
    false
}
println(result) // 출력: data > 0 true
```


## `when` 조건문

`when`은 여러 조건을 효율적으로 처리할 때 사용한다. **자바의 `switch` 문**과 유사하다.

```java
var data = 10

when (data) {
    10 -> println("data is 10")
    20 -> println("data is 20")
    else -> println("data is not valid data")
}
```

### `when` 활용 예제

- **`is` 연산자**로 타입 확인
- **콤마(,)**를 사용해 여러 값을 처리
- **범위(`in`)**를 사용해 값의 범위 조건을 처리

```java
var data: Any = 10

when (data) {
    is String -> println("data is String")
    20, 30 -> println("data is 20 or 30")
    in 1..10 -> println("data is 1..10") // 1 ~ 10 사이의 값
    else -> println("data is not valid")
}
```


### `when` 표현식

- `when`도 Kotlin에서는 **표현식**으로 사용할 수 있으며, 값을 반환한다.

```java
var data = 10

val result = when {
    data <= 0 -> "data is <= 0"
    data > 100 -> "data is > 100"
    else -> "data is valid"
}
println(result) // 출력: data is valid
```


## 반복문

### `for ... in` 반복문

- `for` 문을 사용해 **범위**나 **컬렉션**의 요소를 순회할 수 있다.

```java
var sum: Int = 0
for (i in 1..10) {
    sum += i
}
println(sum) // 출력: 55
```

