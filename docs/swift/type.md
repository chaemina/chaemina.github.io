---
layout: default
title: 구조체 vs 클래스 vs 열거형 
parent: Swift
nav_order: 12
---


# 구조체 vs 클래스 vs 열거형 
구조체와 클래스 그리고 열거형은 타입을 정의한다. [구조체 글](https://chaemina.github.io/docs/swift/struct/),[클래스 글](https://chaemina.github.io/docs/swift/class/),
[열거형 글](https://chaemina.github.io/docs/swift/enum/) 참조 
{: .fs-6 .fw-300 }


{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 참조 | 값 타입 

### 참조 
데이터를 전달 할 뎨 값의 메모리 위치를 전달한다.

### 값 
데이터를 전달 할 때 값을 복사해서 전달한다.


```swift 
// 저장 프로퍼티를 하나 씩 갖는 값 타입과 참조 타입

struct ValueType {
    var property = 1;
}

class ReferenceType {
    var property = 1;
}


// 상수에 값을 구조체/ 클래스 값을 할당 해주고,
// 변수에 이를 복사 한 뒤, 값의 변화를 확인한다
let structA = ValueType();
var structB = structA
structB.property = 2

// 값 타입은 복사하기 때문에 기존의 값이 변하지 않음
print("\(structA.property) \(structB.property)") // 1 2


// 참조 타입은 메모리 위치를 가져오기 때문에 기존의 값 까지 변화함
let classA = ReferenceType();
var classB = classA
classB.property = 2

print("\(classA.property) \(classB.property)") // 2 2
```

## 구조체 vs 클래스 vs 열거형 


|         |    구조체      |  클래스 |  열거형   |
|:-------------|:------------------|:------------------|:------------|
| 타입   | 값 | 참조  | 값 |
| 상속 | x  |  o | x |
| extension |  o  |  o  | o |


### 구조체 

- 값 타입 
- 연관된 몇몇의 값들을 모아서 하나의 데이터 타입으로 표현하고 싶을 때 
- 다른 객체 또는 함수 등으로 전달 될 때, 참조가 아닌 복사를 원할 때 
- 자신을 상속 할 필요가 없거나, 자신이 다른 타입을 상속 받을 필요가 없을 때 
- 애플 프레임 워크에서 프로그래밍 할 땐 주로 클래스를 사용 


### 클래스 

- 참조 타입 
- 전통적인 OOP 관점에서의 클래스 
- 단일 상속 
- 메소드 
- 프로퍼티 
- 애플 프레임 워크 대부분의 큰 뼈대는 모두 클래스로 구성 


### 열거형 

- 값 타입 
- 상속 불가 
- 메소드 
- 연산 프로퍼티 
- 유사한 종류의 여러 값을 유의미한 이름으로 한 곳에 모아 정의 
- 열거형 자체가 하나의 데이터 타입, 열거형의 케이스 하나하나 전부 유의미한 값으로 취급 
