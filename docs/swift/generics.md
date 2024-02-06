---
layout: default
title: 제네릭 
parent: Swift
nav_order: 24
---


# 제네릭
{: .no_toc }


타입에 의존하지 않는 범용 코드를 작성 할 때 사용한다. 
{: .fs-6 .fw-300 }





## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Generics

### 제네릭 장점 

- 중복 코드를 피한다. 
- 코드를 유연하게 작성 할 수 있다. 

스위프트 표준 라이브러리의 대다수는 제네릭으로 선언되어 있다. 


### 제네릭 작성 

```swift
func sumInts(_ a: inout Int, _ b: inout Int) {
   let sum = a + b 
}
```

Int형 인자만 받을 수 있고, 만약 다른 타입의 값들도 받고 싶을 땐 오버라이딩 해야한다. 
<br/>
이때 제네릭을 사용하면 

```swift
func sumInts<S>(_ a: inout S, _ b: inout S) {
   let sum = a + b 
}
```
 `<타입이름>` : 타입 이름은 각자 지정하면 된다. 지정한 타입 이름을 타입 처럼 사용할 수 있다. 
<br/>
이때 타입 이름을 타입 파라미터라고 부르는데, S라는 새로운 형식이 생성된 것이 아니라 실제 함수가 호출 될 때 해당 매개변수 타입으로 대체되는 placeholder(자리타입)이다. 

<br/>
결국 제네릭을 사용하면, 실제 함수를 호출 할 때 타입 파라미터인 S의 타입이 결정된다. 


{: .note-title }
> **주의**
>
> a와 b의 타입 파라미터가 동일한 경우 동일한 타입을 받아야 한다. 

### 명명 규칙 

1. 보통 단일 문자나 카멜 케이스로 작성한다. 
2. 한 개 이상의 경우 `<S,T>` 콤마로 구분한다. 