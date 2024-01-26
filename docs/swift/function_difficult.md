---
layout: default
title: 6. 함수 심화 
parent: Swift
---


# 함수
{: .no_toc }

Swift는 함수형 프로그래밍 패더라임을 포함하는 다중 패러다임 언어이다.
Swift에서 함수는 일급 객체이므로 변수, 상수 등에 저장이 가능하고 매개변수를 통해 전달 될 수 있다.
{: .fs-6 .fw-300 }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## Function 심화 

### 1. 함수 생성하기 

 `func 함수이름 (매개변수: 매개변수타입) -> 반환타입 { ... return 반환값 }`

```swift
func functionA(a:Int, b:Int) -> Int { return a+b}

functionA(a:2, b:4)
```

### 2. 반환값 없는 함수 생성하기 

(1) 반환 타입 void 
```swift
func functionB(a: String) -> Void { print(a)}
```

(2) 반환 타입 생략 
```swift
func functionC(a: String) { print(a)}
```

### 3. 매개변수 없는 함수 생성하기 

```swift
func functionD() -> Int { return 1}
```

### 4. 반환값과 매개변수 모두 없는 함수 생성하기 

(1) 반환 타입 void 
```swift
func functionE() -> Void{ print("hello")}
```

(2) 반환 타입 생략 
```swift
func functionF() { print("hello")}

functionF() // 호출 
```


