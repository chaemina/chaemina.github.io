---
layout: default
title: 인스턴스 생성과 소멸 
parent: Swift
nav_order: 16
---


# 인스턴스 생성과 소멸  
{: .no_toc }

스위프트의 모든 인스턴스는 초기화와 동시에 모든 프로퍼티에 유효한 값이 할당되어 있어야 한다.
{: .fs-6 .fw-300 }




## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 인스턴스 생성과 소멸 

프로퍼티에 미리 기본값을 할당 해두면, 인스턴스 생성과 동시에 초기값을 지니게 된다. 

```swift
class PersonA {
    var name = "" // 기본 값 할당
}
```


## 이니셜라이저

```swift
class PersonB {
    var name : String
    var nickName : String
    // 이니셜 라이저
    init(name: String, nickName: String) {
        self.name = name
        self.nickName = nickName
    }
}
let mina : PersonB = PersonB(name: "mina", nickName: "mi na")
// 만약 닉네임 없을 경우?
let sunny : PersonB = PersonB(name: "sunny", nickName: "")
// -> 매번 호출하면서 초기화 해주시 불편하다
```

프로퍼티 기본 값을 지정하기 어려운 경우에는, 이니셜라이저를 통해 인스턴스가 가져야 할 초기값을 전달 할 수 있다.

### 옵셔널 

`?` 프로퍼티의 초기값이 꼭 필요 없을 때 사용한다. (인스턴스에서 프로퍼티를 사용하지 않을 수 있을 때)

```swift
class PersonC {
    var name : String
    var nickName : String? // 초기화 되지 않을 수 있음을 옵셔널로 표현
    
    // 이니셜 라이저
    // name, nickname
    // convenience 자신의 init 을 가져다 쓸 때 붙여줘야 함
    convenience init(name: String, nickName: String) {
        self.init(name: name) // ==  self.name = name
        self.nickName = nickName
    }
    
    // name 만
    init(name: String) {
        self.name = name
    }
}

let sunny : PersonC = PersonC(name: "sunny")
```

### 암시적 추출 옵셔널 

`!` 인스턴스 사용에는 꼭 필요하지만, 초기값을 할당하지 않고 싶을 때 사용한다. (인스턴스에서 프로퍼티를 꼭 사용해야 할 때)

```swift
class Puppy {
    var puppy : String
    var person : PersonC! 
    
    init(puppy: String) {
        self.puppy = puppy
    }
    
    func goOut() {
        print("\(puppy)가 주인 \(person.name)와 산책을 합니다.")
    }
}

let dongdong : Puppy = Puppy(puppy: "dong dong")
// dongdong.goOut()  person값 초기화 되지 않아서 오류
dongdong.person = sunny
dongdong.goOut()
```

### 실패 가능한 이니셜라이저 

```swift
class PersonD {
    var name : String
    var age : Int
    
    init?(name: String, age: Int) {
        if(0...120).contains(age) == false {
            return nil
        }
        
        self.name = name
        self.age = age
    }
}

let mina : PersonD? = PersonD(name: "mina", age: 21) // 옵셔널 타입
let sunny : PersonD? = PersonD(name: "sunny", age: 222)

print(sunny?.name) //  nil
```

이니셜라이저 매개변수로 전달 되는 초기값이 잘못 된 경우, 인스턴스 생성에 실패 할 수 있다. <br/>
인스턴스 생성에 실패하면 nul을 반환하도록 한다. 실패 가능한 이니셜라이저의 반환 타입은 옵셔널이다. 



## 디이니셜라이저 

```swift
class PersonE {
    var name : String
    var fruit : Fruit?
    
    init(name: String, fruit: Fruit? = nil) {
        self.name = name
        self.fruit = fruit
    }
    
    deinit{
        if let fruitName = fruit?.name {
            print("\(name)가 더이상 \(fruitName)를 먹을 수 없습니다.")
        }
    }
}

var myfruit : PersonE? = PersonE(name:"mina")
myfruit?.fruit = apple
myfruit = nil   // mina가 더이상 apple를 먹을 수 없습니다.
```

`deinit`은 클래스의 인스턴스 메모리에서 해제되는 시점에 호출되어야 한다. <br/>
인스턴스가 해제되는 시점에서 해야 할 일을 구현 할 수 있다. 