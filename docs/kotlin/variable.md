---
layout: default
title: 변수 선언과 할당
parent: Kotlin
nav_order: 2
---

# 변수 선언과 할당
{: .no_toc }

Kotlin에서 변수 선언 방식과 초기값 할당 방법을 배워본다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 변수 선언 타입

`val(var) 변수명 : 타입 = 값`

- `val` : **불변 변수**, 한 번 초기화되면 값을 변경할 수 없다
- `var` : **가변 변수**, 초기화된 이후에도 값을 변경할 수 있다

## 초기값 할당

```java
val data1 : Int // 오류 -> 최상위에 선언한 변수는 선언과 동시에 초기값 할당해야함 
var data2 : Int = 10 // 성공 

fun someFun() {
    val data3 : Int 
    data3 = 10 
    println("Date3 : $data3") // 성공 -> 함수 내부에 선언한 변수는 선언과 동시에 할당 안해도됨
}

class User {
    val data4 : Int // 오류 -> 클래스의 멤버 변수는 선언과 동시에 초기값 할당해야함
    val data5 : Int = 10 // 성공 
}
```


## 초기화 미루기 
`lateinit` 키워드 사용 
- `var` 키워드로 선언한 변수에만 사용 가능
- `String` 및 `Char` 타입에서만 사용 가능

```java
lateinit var name: String

fun initialize() {
    name = "Kotlin"
    println("name: $name") // Kotlin
}
```

`by lazy { }` 키워드 사용 
- 변수가 최초로 사용될 때 초기화
- 중괄호 블록의 마지막 줄이 초기값으로 사용된다

```java
val lazyData: Int by lazy {
    println("초기화 중...")
    100 // 초기값
}

fun main() {
    println(lazyData) // 초기화 중... 100
}
```

## Kotlin 변수 

코틀린의 모든 변수는 객체로 다뤄진다. 기본 자료형도 객체로서 메서드를 가질 수 있다.

```java
var data1 : Int? = Null // null 허용
var data2 : Int = 10 

data2 = data2.plus(10) // 객체 메서드 호출 가능
```

- `Int, Short, Long, Double, Float, Byte, Boolean` : 기초 타입 객체 
- `Char, String` : 문자와 문자열 
- `Any` : 모든 타입의 상위 타입
- `Unit` : 반환문이 없는 함수의 반환 타입
- `Nothing` : null 반환이나 예외 처리에서 사용