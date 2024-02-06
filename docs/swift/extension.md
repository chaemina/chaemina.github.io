---
layout: default
title: 익스텐션
parent: Swift
nav_order: 21
---


# 익스텐션 
{: .no_toc }


구조체, 클래스, 열거형, 프로토콜 타입에 새로운 기능을 추가할 수 있는 기능이다. 기능을 추가하려는 타입의 구현 된 소스 코드를 알지 못하거나 보지 못해도 타입만 알고 있으면 가능하다. 
{: .fs-6 .fw-300 }





## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## extension

### 익스텐션으로 추가 할 수 있는 기능 

- 연산 타입 프로퍼티 / 연산 인스턴스 프로퍼티 
- 타입 메소드 / 인스턴스 메소드 
- 이니셜 라이저 
- 서브 스크립트 
- 중첩 타입 
- 특정 프로토콜에 준수 할 수 있도록 기능 추가 

{: .warning}
단, 기능에 존재하는 기능을 재정의 할 순 없다. 

## 익스텐션 정의 

 `extension 확장할 타입 이름 { 내용 }`

### 연산 인스턴스 프로퍼티 추가 

```swift
extension Int {
    var isEven: Bool {
        return self%2 == 0
    }
    var isOdd: Bool {
        return self%2 == 1
    }
}

print(1.isEven) // F
print(1.isOdd) // T
print(2.isEven) // T
print(2.isOdd) // F

var number : Int = 3
print(number.isEven) // F
print(number.isOdd) // T
```

Int 타입에 연산 프로퍼티 기능을 추가한다. Int 타입의 값들에서 프로퍼티 사용이 가능하다. 

### 연산 메소드 추가 

```swift
extension Int {
    func multiply(n: Int) -> Int {
        return self*n
    }
}
print(2.multiply(n: 10)) // 20

var number : Int = 3
print(number.multiply(n: 2)) // 6
```

Int 타입에 연상 메소드 기능을 추가한다. Int 타입의 값들에서 메소드 사용이 가능하다. 


### 이니셜라이저 

```swift
extension String {
    init(n: String){
        self = "\(n)"
    }
}

let str : String = String(n:"init") // "init"
```
익스텐션으로 모든 문자열 타입의 이니셜라이저를 처리한다. 


