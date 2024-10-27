---
layout: default
title: 컬렉션 타입
parent: Kotlin
nav_order: 4
---

# 컬렉션 타입
{: .no_toc }

컬렉션 타입의 종류와 사용법을 학습한다. 
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array

- **`Array` 클래스** 생성자:
  - 첫 번째 매개변수: 배열의 크기
  - 두 번째 매개변수: 초기값
- 배열에 접근할 때 **대괄호**(`[]`) 또는 **set, get** 함수를 사용 가능

```java
val arr: Array<Int> = Array(3) { 0 }
arr[0] = 10
arr[1] = 20
arr.set(2, 30)

println(arr.size) // 3
println(arr.get(2)) // 30
```

### `arrayOf` 함수로 배열 선언 및 값 할당

```java
val arr = arrayOf<Int>(10, 20, 30)
```


## List
- **순서가 있는 데이터 집합**, 데이터의 **중복 허용**
- `listOf`: **불변 리스트**
- `mutableListOf`: **가변 리스트**

```java
var list = listOf<Int>(10, 20, 30) // 불변 리스트

println(list.size) // 3
println(list[0]) // 10
println(list.get(1)) // 20

var mutableList = mutableListOf<Int>(10, 20, 30) // 가변 리스트
mutableList.add(3, 40)
mutableList.set(1, 10)

println(mutableList.size) // 4 (값 추가됨)
```


## Set
- **순서가 없는 데이터 집합**, **중복 허용하지 않음**

```java
val set = setOf<Int>(1, 2, 3, 3) // 중복된 값은 하나만 유지됨
println(set.size) // 3
```

## Map
- **키-값으로 이루어진 데이터 집합**, **순서가 없으며 키의 중복은 허용하지 않음**

#### `Map` 선언 방식
- **`Pair` 객체** 사용
- **`키 to 값` 형태**로 선언

```java
var map = mapOf<String, String>(Pair("One", "hello"), "Two" to "world")

println(map.size) // 2
println(map.get("One")) // hello
println(map.get("Two")) // world
```
