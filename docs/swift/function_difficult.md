---
layout: default
title: 6. 함수 심화 
parent: Swift
---


# 함수 심화
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

### 1. 기본 값을 갖는 매개변수 

```swift
func functionA(a: String, b: String = "기본값") {
    print("a : \(a), b: \(b)")
}

functionA(a: "hello") //a : hello, b: 기본값 , a의 값만 전달해줘도 된다.
functionA(a: "hello", b: "world") // a : hello, b: world
```

기본 값을 갖는 매개변수를 뒤쪽에 위치 시키는 것을 권장한다. 
기본 값을 이미 갖고 있기 때문에 값을 전달하지 않아도 되지만, 전달 해주어도 된다.


### 2. 전달 인자 레이블 

 `func 함수이름(전달인자 레이블  매개변수 이름 : 매개변수 타입 ) -> 반환타입 { ... return 반환값 }`

```swift
func functionB(to a: String, from b: String) {
    print("helllo \(a)! I'm \(b)")
}

functionB(to: "hana", from: "mina") // 호출 할 때는 전달 인자 레이블 사용
```

매개 변수의 역할을 더 명확히 하거나 사용자 입장에서 표현 할 때 사용된다. 


### 3. 가변 매개변수 

```swift
func functionC(a: String, b: String...) {
    print( "hello \(b)! I'm \(a)")
}

functionC(a: "mina", b: "hana", "yusun")
//hello ["hana", "yusun"]! I'm mina
functionC(a: "mina") // b: 이나, b: nil 의 경우는 오류 발생
//hello []! I'm mina
```

전달 받는 값의 개수를 알기 어려울 때 사용된다. 
<br/>
❗ **주의** 함수 당 하나의 가변 매개변수만을 가질 수 있다.  


### 4. 데이터 타입으로서의 함수 

 `var 변수이름 : (매개변수1타입,매개변수2타입) -> 반환 타입 = 함수(매개변수1이름:매개변수2이름)`

```swift
func functionA(a: String, b: String = "기본값") {
    print("a : \(a), b: \(b)")
}

var functionB: (String,String) -> Void = functionA(a:b:)
```

함수 functionA를 변수 functionB에 대입하면, 변수 functionB는 함수 functionA와 같은 기능을 한다.
<br/>
❗ **주의** 반환 타입을 생략 할 수 없다.   


 `func 함수이름 : (매개변수1타입,매개변수2타입) -> Void { }`

```swift
func functionC(a: (String, String)-> Void) {
    a("hello","mina")
}
functionC(a: functionA(a:b:))
```

함수의 매개 변수 인자로 함수를 받을 수 있다. 

