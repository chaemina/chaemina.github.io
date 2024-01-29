---
layout: default
title: 9-1. 클래스
parent: Swift
---


# 클래스 
{: .fs-6 .fw-300 }


{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 구조체와 클래스의 차이 



|    구조체     |    클래스      | 
|:-------------|:------------------|
| 값 타입   | 참조 타입 |   
| `static` | `static` (재정의 불가) `class` (재정의 가능)   | 
| 구조체 선언 변수 `var`   | 클래스 선언 변수 `var` `let`      | 


## class 

### 클래스 작성 

```swift
class Student {
    var name : String = "name"
    var age : Int = 0
    static var interest : String = "interest"
    
    
    class func typeMethodA() {
        print("재정의 가능한 타입 메소드입니다.")
    } // 상속 받은 클래스에서 오버라이딩
    
    
    static func typeMethodB() {
        print("재정의 불가한 타입 메소드입니다.")
    }
    
    func instanceMethod() {
        print("저는 \(age)살 \(name) 입니다.")
    }
}
```
{: .note-title }
> 클래스 Student 
>
> 인스턴스 프로퍼티 : String 타입의 name, Int 타입의 age (둘다 가변) <br/> 타입 프로퍼티 : String 타입의 interest <br/> class 타입 메소드 : typeMethodA() <br/> static 타입 메소드 : typeMethodB() <br/> 인스턴스 메소드 : instanceMethod()

### 클래스 접근 

- **타입 프로퍼티, 메소드 접근** 

```swift
Student.interest = "책읽기"
Student.typeMethodA()
```

바로 접근이 가능하다. 

- **인스턴스 프로퍼티, 메소드 접근** 

```swift
let mina: Student = Student()
mina.name = "민아"
mina.age = 21
mina.instanceMethod()
```

let 키워드로 변수 선언 후 프로퍼티 지정이 가능하다. 


