---
layout: default
title: 데이터 타입 
parent: Swift
nav_order: 3
---


# 데이터 타입 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## data type

- Bool 
불리언 (0,1 로 표현 불가)
- Int 
정수 
- UInt 
양의 정수 
- Float 
실수 
- Double 
실수 (정수값 가능, Float 변수 값 넣을 순 없음)
- Character 
문자 (큰 따옴표)
- String
문자열 (큰 따옴표, 연산으로 문자열 결합 가능, 캐릭터 변수 값 넣을 순 없음)

{: .note-title }
> **주의**
>
> 스위프트에선 다른 데이터 타입 간의 자료 교환이 암시적으로 불가능하다. 

## keyword

### 타입을 대신하는 키워드 

### Any
Swift의 모든 타입을 지칭 하는 키워드

```swift
var someAny : Any = 100
someAny = "어느 타입의 값이든 가능하다."
```

### AnyObject
모든 클래스 타입을 지칭하는 프로토콜

```swift
class SomeClass {}
var someAnyObject : AnyObject = SomeClass()
```


### nil
없음을 의미

{:.warning}
Any와 AnyObject 의 값으로 nil은 넣을 수 없다.



