---
layout: default
title: 9-9. 타입 캐스팅 
parent: Swift
---


# 타입 캐스팅  
{: .fs-6 .fw-300 }


{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 타입 캐스팅

인스턴스의 타입을 확인하하거나 부모 혹은 자식 클래스의 타입으로 사용할 수 있는 지 확인한다. 

```swift
class Person {
    var name : String = ""
    func breath() {
        print("숨을 쉽니다.")
    }
}

class Student: Person {
    var school : String = ""
    func goToSchool() {
        print("등교를 합니다")
    }
}

class Univ: Student {
    var major : String = ""
    func goToMT() {
        print("엠티를 갑니다.")
    }
}

var mina : Person = Person()
var sunny : Student = Student()
var hana : Univ = Univ()
```

`is` 를 사용하여 타입을 확인한다. 

```swift
// 인스턴스 is 클래스 
var result : Bool

result = mina is Person // T
result = mina is Student // F
result = mina is Univ  // T

result = sunny is Person // T
result = sunny is Student // T
result = sunny is Univ // F

result = hana is Person // T
result = hana is Student // T
result = hana is Univ //T

mina is Univ ? print("mina는 대학생") : print("mina는 사람")
```

{: .note-title }
> **주의**
>
> 스위치 문을 사용할 때, 셋 다 해당 되는 경우 가장 먼저 만나는 조건에서 멈춘다. 



## 업캐스팅

## 다운 캐스팅 


