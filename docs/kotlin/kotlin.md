---
layout: default
title: Kotlin
nav_order: 5
has_children: true
permalink: docs/kotlin
---

# Kotlin
{: .no_toc }

Kotlin에 대한 학습 내용은 **모바일 응용 소프트웨어** 과목을 수강하며 정리하였다.

Kotlin이란?
{: .fs-6 .fw-300 }
Kotlin은 JetBrains에서 개발하고 Google이 공식 지원하는 오픈 소스 프로그래밍 언어로, 주로 Android 애플리케이션과 서버 개발에 사용된다.

왜 Kotlin을 사용할까?
{: .fs-6 .fw-300 }

### 간결함 

Kotlin은 기존 Java보다 적은 코드로 작성할 수 있어 간결하고 효율적인 코딩을 가능하게 한다.

### Java와의 호환성

Kotlin은 JVM(Java Virtual Machine)에서 실행되므로 기존 Java 코드와 완전히 호환되며, Java와 함께 사용할 수 있다.

### 안전성 

널 참조 오류(NullPointerException)를 방지하는 다양한 기능을 제공하여 코드의 안정성을 높인다.

### 확장 가능성

Kotlin은 함수형 프로그래밍 스타일을 지원하며, 확장 함수 등을 통해 유연하고 확장 가능한 코드를 작성할 수 있다.

# Kotlin 파일 구성 

```java
package com.example.test3 // 패키지 -> 모두 소문자, 밑줄 없이 

import java.util.* // import 

val data = 10, // 변수, 가능한 한 val과 불변 컬렉션 사용 

fun formatData(date : Date) : String { // 함수 및 속성 -> 소문자 카멜표기법 
    val sdformat = SimpleDateFormat("yyyy-mm-dd") 
    return sdformat.format(date)
}

class User { // 클래스 및 객체 -> 대문자 카멜표기법 UserClass 
    val name = "hello",
    
    fun sayHello() {
        println("name :$name")
      }
}
```
