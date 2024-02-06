---
layout: default
title: 프로토콜 
parent: Swift
nav_order: 20
---


# 프로토콜 
{: .no_toc }


프로토콜은 특정 역할을 수행하기 위한 메소드, 프로퍼티, 이니셜 라이저등의 요구 사항을 정의한다. 구조체, 클래스, 열거형은 프로토콜을 채택해서 프로토콜의 요구사항을 실제로 구현 할 수 있다. 
어떤 프로토콜의 요구사항을 모두 따르는 타입은 **프로토콜을 준수한다**고 표현한다. 프로토콜의 요구사항을 충족시키려면 프로토콜이 제시하는 기능을 모두 구현해야 한다. 
{: .fs-6 .fw-300 }





## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Protocol 

 `protocol 프로토콜 이름 { 정의 }`

### 프로토콜 정의 

```swift
protocol Talkable {
    //프로퍼티 요구는 항상 변수로 선언
    var topic : String { get set }
    var language : String { get }
    
    // 메소드 요구
    func talk()
    
    // 이니셜 라이저 요구
    init(topic: String, language: String)
}
```


### 프로토콜 채택 및 준수 

```swift
struct Person: Talkable {
    var topic: String
    let language: String // var 키워드도 가능
    
    // 저장 프로퍼티의 경우 연산 프로퍼티로 작성 할 수 있다.
    func talk() {
        print("\(topic)에 대해 \(language)로 말합니다.")
    }
    
    init(topic: String, language: String) {
        self.topic = topic
        self.language = language
    }
}
```

### 프로토콜 상속 

{: .highlight}
프로토콜은 클래스와 달리 다중 상속이 가능하다. 

```swift
protocol Readable {
    func read()
}

protocol Writeable {
    func write()
}

protocol ReadWriteable: Readable, Writeable {
// read(), write() 메소드 정의 하지 않아도 상속 받아서 가지고 있음
    func speak()
}
```

```swift
// 활용 
struct Person: ReadWriteable {
    func read() {
        print("read")
    }
    func write() {
        print("write")
    }
    func speak() {
        print("speak")
    }
}

var readAndWrite : Person = Person()

readAndWrite.read()
readAndWrite.write()
readAndWrite.speak()
```


{: .note-title }
> **클래스와 프로토콜 동시에 상속 받는 경우**
>
> `class 클래스 이름 : 부모 클래스 , 프로토콜 { 내용 }` <br/> 부모 클래스를 먼저 명시한다. 

