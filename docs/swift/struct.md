---
layout: default
title: 9. 구조체 
parent: Swift
---


# 구조체 
구조체와 클래스 그리고 열거형은 타입을 정의한다. 구조체와 클래스의 차이는 [클래스 글](https://chaemina.github.io/docs/swift/class/)에서, 열거형까지 셋의 차이는 
[구조체 vs 클래스 vs 열거형 글](https://chaemina.github.io/docs/swift/type/)에서 설명한다.
{: .fs-6 .fw-300 }


{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## struct

 `struct 이름 { ... }`

구조체 안의 변수 : 프로퍼티 
구조체 안의 함수 : 메소드


```swift
struct Sample {
    // 인스턴스 프로퍼티
    var propertyA : Int = 100 // 가변 프로퍼티
    let propertyB : Int = 100 // 불변 프로퍼티
    // 타입 프로퍼티
    static var propertyC : Int = 100
    
    // 인스턴스 메소드
    func methodA() {
        print("instance method")
    }
    // 타입 메소트
    static func methodB() {
        print("type method")
    }
}

// 타입 프로퍼티, 메소드 -> 바로 접근 할 수 있음
Sample.propertyC = 300
Sample.methodB()


// 인스턴스 프로퍼티, 메소드 -> 변수에 할당하고 접근

// 가변 인스턴스
var instanceA : Sample = Sample()
instanceA.propertyA = 200
// instanceA.propertyB = 200 // let keyword 프로퍼티라서 변경 불가
print(instanceA) // Sample(propertyA: 200, propertyB: 100)


// 불변 인스턴스
let instanceB : Sample = Sample()
// instanceB.propertyA = 300 // var 프로퍼티여도 변수가 불변이라 안됨
print(instanceB) // Sample(propertyA: 100, propertyB: 100)

```

## Student 라는 구조체 작성해보기

### 구조체 작성 

```swift
struct Student {
    var name : String = "name"
    var age : Int = 0
    static var interest : String = "interest"
    
    static func typeMethod() {
        print("학생 타입 메소드입니다.")
    }
    
    func instanceMethod() {
        print("저는 \(age)살 \(name) 입니다.")
    }
}
```
{: .note-title }
> 구조체 Student 
>
> 인스턴스 프로퍼티 : String 타입의 name, Int 타입의 age (둘다 가변) <br/> 타입 프로퍼티 : String 타입의 interest <br/> 타입 메소드 : typeMethod() <br/> 인스턴스 메소드 : instanceMethod()

### 구조체 접근 

- **타입 프로퍼티, 메소드 접근** 

```swift
Student.interest = "책읽기"
print(Student.interest)
Student.typeMethod()
```

바로 접근이 가능하다. 

- **인스턴스 프로퍼티, 메소드 접근** 

```swift
var mina: Student = Student()
mina.name = "민아"
mina.age = 21
mina.instanceMethod()
```

Student 구조체 타입의 변수를 선언하고, 구조체를 할당 해준 뒤 해당 변수를 통해 접근이 가능하다. 
