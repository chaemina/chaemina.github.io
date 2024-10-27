---
layout: default
title: ETC
parent: Kotlin
nav_order: 7
---

# ETC
{: .no_toc }

Kotlin에서 객체 데이터 비교, 널 안정성 처리, 예외 발생 등을 학습한다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 객체 데이터 비교: `equals()`

- **`equals()` 함수**를 사용해 두 객체의 데이터를 비교한다.
- **주 생성자에 선언된 멤버 변수의 데이터**만 비교 대상이 된다.

```java
val obj1 = User("chae", 10)
val obj2 = User("chae", 10)

println(obj1.equals(obj2)) // true 또는 false, 멤버 변수 데이터로 비교
```


## 객체의 데이터를 반환하는 `toString()`

- **`toString()` 함수**는 객체의 데이터를 문자열 형태로 반환한다.

```java
val obj = User("chae", 10)
println(obj.toString()) // 출력: User(name=chae, count=10)
```


## 널 안정성 (Null Safety)

Kotlin에서는 **널 포인트 예외**를 방지하기 위해 **널 안정성** 관련 기능을 제공한다.



### `?.` 연산자

- 널 허용 변수의 멤버에 접근할 때 **`?.` 연산자**를 사용한다.

```java
var data: String? = null
val length = if (data == null) {
    0
} else {
    data.length
}
println("data length: $length") // 출력: 0
```

- **위 코드와 동일한 표현**:

```java
println("data length: ${data?.length ?: 0}")
```


### 엘비스 연산자 `?:`

- **`?:` 연산자**는 값이 널일 때 사용할 **대체 값이나 구문**을 정의할 수 있다.

```java
var data: String? = "chae"
println("data = $data : ${data?.length ?: -1}") // null일 경우 -1 출력
```


## 예외 발생: `!!`

- **`!!` 연산자**를 사용해 객체가 널일 경우 **NullPointerException** 예외를 발생시킨다.

```java
fun some(data: String?): Int {
    return data!!.length
}

some(null) // 예외 발생: Exception in thread ~ NullPointerException
```

