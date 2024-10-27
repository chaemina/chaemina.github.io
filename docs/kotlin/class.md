---
layout: default
title: 클래스
parent: Kotlin
nav_order: 6
---

# 클래스
{: .no_toc }

Kotlin에서 클래스 선언과 사용법을 학습한다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 클래스 선언

Kotlin에서는 `class` 키워드로 클래스를 선언한다.  
클래스는 다음과 같은 **멤버**로 구성될 수 있다:

- **생성자**
- **변수**
- **함수**
- **클래스**


### 주 생성자와 `init` 키워드

- **`init` 키워드**로 주 생성자 본문을 구현하며, 객체 생성 시 자동 실행된다.

```java
class User(name: String, count: Int) {
    init {
        println("I am init...")
    }
}

val user = User("chae", 10) // 출력: I am init...
```

- **매개변수에 `val` 키워드**를 선언하면, 클래스 내부에서 해당 매개변수를 사용할 수 있다.  
  그렇지 않으면 **생성자 내부에서만 사용 가능**하다.


### 보조 생성자

- **`constructor` 키워드**로 보조 생성자를 선언할 수 있다.

```java
class User {
    constructor(name: String) {
        println("First constructor call")
    }

    constructor(name: String, count: Int) {
        println("Second constructor call")
    }
}
```


### 주 생성자와 보조 생성자 연결

- 보조 생성자가 주 생성자를 호출하는 예제:

```java
class User(name: String) {
    constructor(name: String, count: Int) : this(name) {
        // 주 생성자를 호출
    }
}
```


## 상속과 생성자

- Kotlin에서는 기본적으로 **클래스를 상속할 수 없다**.
- **상속이 가능하도록 하려면 `open` 키워드**를 사용해야 한다.
- **하위 클래스의 생성자**에서는 반드시 **상위 클래스의 생성자**를 호출해야 한다.



### 매개변수가 있는 상위 클래스 생성자 호출

```java
open class Super(name: String)

class Sub(name: String) : Super(name) // 클래스와 생성자 동시에 상속
```

### 보조 생성자와 상속

- **보조 생성자**에서 상위 클래스의 생성자를 호출하는 예제:

```kotlin
open class Super(name: String)

class Sub : Super {
    constructor(name: String) : super(name) {
        // super 키워드로 상위 클래스 생성자 호출
    }
}
```



## 오버라이딩 (Overriding) - 재정의

- 상위 클래스의 멤버를 하위 클래스에서 **재정의**하여 사용할 수 있다.
- **`open` 키워드**로 상위 클래스의 멤버를 열어주고, 하위 클래스에서는 **`override` 키워드**로 재정의한다.

```java
open class Super {
    open var someData = 10
    open fun someFun() {
        println("I am super class $someData")
    }
}

class Sub : Super() {
    override var someData = 20
    override fun someFun() {
        println("I am sub class $someData")
    }
}

val obj = Sub()
obj.someFun() // 출력: I am sub class 20
```


## 접근 제어자

- **`public`**: 모든 파일과 클래스에서 접근 가능.
- **`internal`**: 같은 모듈 내에서만 접근 가능.
- **`protected`**: **상속 관계**의 하위 클래스에서만 접근 가능.
- **`private`**: **클래스 내부**에서만 접근 가능.



## 익명 클래스 (`object` 키워드)

- **`object` 키워드**를 사용해 익명 클래스를 선언과 동시에 객체로 생성할 수 있다.

```java
val obj = object {
    var data = 10
}

obj.data = 20 // 오류: 익명 객체의 멤버는 재할당 불가
```


## `companion` 객체

- **`companion object`**를 사용하면, 클래스의 **정적 멤버**처럼 변수나 함수를 사용할 수 있다.

```java
class MyClass {
    companion object {
        var data = 10
    }
}

MyClass.data = 20 // 클래스 이름으로 접근 가능
```


