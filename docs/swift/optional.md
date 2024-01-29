---
layout: default
title: Optional
parent: Swift
nav_order: 8
---


# Optional
{: .no_toc }

값이 있을 수도 없을 수도 있다. nil의 가능성을 명시적으로 표현한다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## optional

```swift
func functioA(a: Int?) { ... } // optional
func functionB(a: Int) { ... }

functionA(a: nil) // ok
functionB(a: nil) // error
```

**스위치 문으로 값 여부 확인하기**

```swift
switch optionalValue {
   case .none: 
       print("nil 값을 가질 때")
   case .some(let value):
       print("\(value)라는 값을 가질 때")
}
```

### !

```swift
var optionalValue : Int! = 100

var sum : Int = optionalValue + 1 // 101 
```

암시적 추출 옵셔널로 nil 이 아닐 땐 기존 변수처럼 접근이 가능하다.

### ?

```swift
var optionalValue : Int? = 100

var sum : Int = optionalValue + 1 // error
```

암시적 추출 옵셔널과 달리, 기존 변수처럼 접근이 불가능하다. 



## 그러면 어떻게 옵셔널 값에 접근 할까?

### 1. optional binding : 옵셔널 바인딩 

nil의 경우를 체크하고, 안전하게 값을 추출한다. 

`if-let` 구문 

```swift
var myName : String? = nil // optional로 타입 지정, nil값을 가짐

if let a: String = myName{
    print(a) // a값은 반복문 안에서만 사용 할 수 있음
} else{
    print("myName === nil")
}
```

1개 이상의 옵셔널도 추출 가능 

```swift
var myName : String? = "mina" 
var yourName : String? = "hana"

if let a: String = myName, let b: String = yourName{
    print(a + b) // minahana
} else{
    print("둘 중 하나라도 nil 값일 때")
}
```

{: .note-title }
> **주의**
>
> 단 하나라도 nil 값이면, break

### 2. force unwrapping : 강제 추출

암시적 추출 옵셔널로 선언하거나, 함수에 전달 할 때 변수 명 뒤 `!` 를 붙이는 경우 

{:.warning}
에러가 발생하기 때문에, 권장하지 않는다. 







