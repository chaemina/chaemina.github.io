---
layout: default
title: 클로저 
parent: Swift
nav_order: 13
---


# 클로저 
{: .no_toc }

코드의 블럭, 일급 시민 
{: .fs-6 .fw-300 }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## closure 

변수나 상수 등으로 저장하고 전달 인자로 전달이 가능하다.

### 함수를 사용한 클로저 작성

함수는 이름이 있는 클로저

 `{ (매개변수 목록) -> 반환타입 in 실행코드 }`

```swift
// 함수 정의 
func sumFunction(a: Int, b: Int) -> Int {
    return a+b
}

// 변수에 할당 
var sum : Int = sumFunction(a: 1, : 2)
print(sum) // 3
```

### 클로저의 타입 

 `(매개변수 타입, 매개변수 타입) -> 반환타입`

```swift
// 클로저 정의 
// 변수에 클로저를 할당 
               // 클로저의 타입 표현 
var sumClosure : (Int, Int) -> Int = { (a:Int, b:Int) -> Int in 
    return a+b
}

// 주의 ! 함수를 호출하는 것이 아니니, 매개변수 말고 값만 넣어서 호출하면 됨 
var sum = sumClosure(1,2)
print(sum) //3
```


### 함수의 전달인자로 사용 

```swift
// 상수 선언
let add : (Int, Int) -> Int

// 클로저 할당
add = {(a:Int, b:Int) -> Int in
return a+b}


// 클로저를 매개변수(method)로 전달 받는 함수
func calculate(a:Int, b:Int, method: (Int,Int) -> Int) -> Int {
    return method(a,b)
}

// 함수에 add 클로저 인자로 전달하여 호출
var cal : Int = calculate(a: 1, b: 2,  method: add)
print(cal)
```

### 클로저 문법 축약하기 

**호츌과 동시에 클로저 정의**

```swift
func calculate(a:Int, b:Int, method: (Int,Int) -> Int) -> Int {
    return method(a,b)
}

var cal : Int = calculate(a: 1, b: 2, method: {( a: Int, b: Int ) -> Int in
return a + b })
```

**후행 클로저** 

```swift
var cal : Int = calculate(a: 1, b: 2) {( a: Int, b: Int ) -> Int in
return a + b }
```

클로저가 함수의 마지막 전달 인자라면, 마지막 매개변수 이름을 생략 한 뒤 소괄호 외부에 클로저를 구현 할 수 있다.

**반환 타입 생략** 

```swift
var cal : Int = calculate(a: 1, b: 2 ){( a: Int, b: Int )  in
    return a + b }
```

함수에서 이미 반환 타입을 작성 해놔서 컴퍼일러가 알고 있기 때문에 생략이 가능하다.


**단축 인자 이름** 

```swift
var cal : Int = calculate(a: 1, b: 2 ){ return $0 + $1 }
```

클로저의 매개변수 이름이 굳이 불필요하다면, 단축 인자이름을 활용할 수 있다.<br/>
단축인자 이름은 클로저의 매개변수 순서대로 `$0, $1 ...` 

**암시적 반환 표현** 

```swift
var cal : Int = calculate(a: 1, b: 2 ){ $0 + $1 }
```

클로저가 반환 하는 값이 있다면, 알아서 마지막 줄을 반환하기 때문에 반환 키워드를 생략 할 수 있다. 

{: .note-title }
> **주의**
>
> 다른 사람들이 이해하지 못할 정도로 축약 하지 않도록 주의해야한다. 