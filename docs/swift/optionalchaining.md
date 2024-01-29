---
layout: default
title: 옵셔널 체이닝
parent: Swift
nav_order: 17
---


# 옵셔널 체이닝 
{: .no_toc }

옵셔널 요소 내부의 프로퍼티로, 또 다시 옵셔널이 연속적으로 연결되는 경우 유용하다. 
{: .fs-6 .fw-300 }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 옵셔널 체이닝 

### 클래스 작성 

```swift
class Person {
    var name : String
    var job : String?
    var home : Apartment?
    
    init(name: String) {
        self.name = name
    }
}
class Apartment {
    var roomNumber : String
    var owner : Person?
    
    init(roomNumber: String) {
        self.roomNumber = roomNumber
    }
}
```

### 옵셔널 체이닝으로 접근 

```swift
let mina : Person? = Person(name: "mina")
let apart : Apartment? = Apartment(roomNumber: "222")


mina?.home?.owner?.job // nil
mina?.home = apart
mina?.home // Apartment

mina?.home?.owner // nil
mina?.home?.owner = mina
mina?.home?.owner // Person

mina?.home?.owner?.name // mina
mina?.home?.owner?.job // nil
mina?.home?.owner?.job = "집주인"
mina?.home?.owner?.job
```



## nil 병합 연산자 

```swift
owner = mina?.home?.owner?.job ?? "슈퍼맨" 
```

`??` 값이 nil 이면 해당 값을 반환한다. 
