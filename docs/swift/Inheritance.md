---
layout: default
title: 상속
parent: Swift
nav_order: 15
---


# 상속
{: .no_toc }


스위프트 상속은 클래스와 프로토콜 등에서 가능하다. (열거형, 구조체는 상속 불가) 
스위프트는 다중 상속을 지원하지 않는다. 
{: .fs-6 .fw-300 }





## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 상속

 `class 이름 : 부모 클래스 이름 { 내용 }`

- 저장 프로퍼티 재정의 불가 
- `final` `static` 재정의 불가 
- `final class` 는 `static`과 같은 역할, 재정의 불가 
- `class` 재정의 가능 

### 부모 클래스 


```swift
class Person {
    
    // 인스턴스 저장 프로퍼티
    var name : String = ""  // 재정의 불가
    
    // 인스턴스 메소드
    
    func selfIntro() {
        print("저는 \(name) 입니다.")  // 재정의 가능
    }
    
    final func sayHello() {
        print("hello")   // 재정의 불가
    }
    
    // 타입 메소드
    
    static func typeMethod() {
        print("type method - static") // 재정의 불가
    }
    
    class func classMethod() {
        print("type method - class") // 재정의 가능
    }
    
    final class func finalClassMethod() {
        print("type method - final class") // 재정의 불가
    }
    
}
```

### 자식 클래스

```swift
class Student: Person {
   // var name : String = "" 저장 프로퍼티는 재정의 불가
    var major : String = "" // 새로운 프로퍼티 생성
    
    override func selfIntro() {
        print("저는 \(name)이고, 전공은 \(major)입니다.") // 인스턴스 메소드 재정의
        super.selfIntro() // 부모 클래스 메소드 호출
    }
    
    override class func classMethod() {
        print("overriden type method - class")  // 클래스 타입 메소드 재정의
    }
    
//    override final func sayhello() {}  final 키워드 재정의 불가
//    override static func typeMethod() {}  static 타입 메소드 재정의 불가
//    override class func finalClassMethod() {}  final class 타입 메소드 재정의 불가
}
```

### 부모 자식 클래스 접근 

```swift
let mina : Person = Person()
let sunny : Student = Student()

mina.name = "mina"
sunny.name = "sunny"
sunny.major = "sw"

mina.selfIntro() //저는 mina 입니다.
sunny.selfIntro() // 저는 sunny이고, 전공은 sw입니다.

// type method
Person.classMethod() // type method - class
Person.typeMethod() // type method - static
Person.finalClassMethod() // type method - final class

Student.classMethod() // overriden type method - class
Student.typeMethod() // type method - static
Student.finalClassMethod() // type method - final class
```