---
layout: default
title: 5. 함수 
parent: Swift
---


# 함수
{: .no_toc }

swift에서의 기초적인 함수 문법을 설명한다.
{: .fs-6 .fw-300 }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## Function 

### 1. 함수 생성하기 

 `func 함수이름 (매개변수: 매개변수타입) -> 반환타입 { ... return 반환값 }`

```swift
func functionA(a:Int, b:Int) -> Int { return a+b}

functionA(a:2, b:4)
```


### 2. 반환값 없는 함수 생성하기 

1️⃣ 반환 타입 void 
```swift
func functionB(a: String) -> Void { print(a)}
```

<br/>

2️⃣ 반환 타입 생략 
```swift
func functionC(a: String) { print(a)}
```

<br/>

### 3. 매개변수 없는 함수 생성하기 

```swift
func functionD() -> Int { return 1}
```

<br/>

### 4. 반환값과 매개변수 모두 없는 함수 생성하기 

1️⃣ 반환 타입 void 
```swift
func functionE() -> Void{ print("hello")}
```

2️⃣ 반환 타입 생략 
```swift
func functionF() { print("hello")}

functionF() // 호출 
```


