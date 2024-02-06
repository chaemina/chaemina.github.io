---
layout: default
title: assert 와 guard 
parent: Swift
nav_order: 19
---


# assert 와 guard 
{: .no_toc }


앱이 동작 도중에 생성하는 다양한 결과 값을 동적으로 확인하고 안전하게 처리 할 수 있도록 한다. 
{: .fs-6 .fw-300 }





## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Assertion

 `assert(condition: Bool, message: String)` 

```swift
var someInt : Int = 0

assert(someInt == 0, "someInt!=0")

someInt = 1

assert(someInt == 0, "someInt!=0")
```
 <img src="../../../assets/images/assert1.png" alt="assert Image" aria-label="assert Image" width="600" height="600">

{: .warning}
디버딩 모드에서만 작동한다. 


### 매개변수로 들어오는 값 검증할 때 사용 

```swift
// 매개변수 타입이 옵셔널이기 때문에, nil값이 들어올 수 있음
func functionAge(age: Int?){
    
    // age 값이 nil이 아닐 때만, 함수가 작동하도록 함
    assert(age !=  nil, "age == nil")
    assert((age! >= 0) && (age! <= 130), "나이값 입력이 잘못되었습니다.")
    print("당신의 나이는 \(age!)세 입니다.")
}

functionAge(age: 50)
functionAge(age: -1)
functionAge(age: nil)
```

 <img src="../../../assets/images/assert2.png" alt="assert Image" aria-label="assert Image" width="600" height="600">


## guard

**Early Exit** 잘못 된 값 전달 시 특정 실행 구문을 빠르게 종료한다. 

{: .warning}
guard의 else 블럭 내부에는 특정 코드 블럭을 종료하는 지시어(return, break 등)가 꼭 있어야 한다. 

```swift
func functionAge(age: Int?){
    
    guard let unwrappedAge = age,
          unwrappedAge < 120,
          unwrappedAge >= 0 else {
        print("나이 값 입력이 잘못되었습니다.")
        return
    }
    
    guard unwrappedAge == 22 else {
        print("당신의 나이는 \(unwrappedAge)세 입니다.")
        return
    }
    print("생일 축하 합니다!")
}
```
```swift
functionAge(age: 50) // 당신의 나이는 50세 입니다.
functionAge(age: -1) // 나이 값 입력이 잘못 되었습니다. 
functionAge(age: nil) // 나이 값 입력이 잘못 되었습니다. 
functionAge(age: 22) // 생일 축하 합니다!
```

assert의 경우 강제 종료되며 에러가 발생하는데, guard의 경우 if else 구문처럼 특정 조건을 벗어나는 경우 구문이 실행된다. 
assert는 정말 들어가면 안되는 값들에 대한 검사, guard의 경우 조건문 처럼 사용할 수 있다. 

### 활용 

**반복문에서의 조건**

```swift
var cnt = 1

while true {
    guard cnt < 3 else {
        break
    }
    print(cnt)
    cnt += 1
}
```
cnt 값이 3보다 작지 않은 경우 break한다. 

**캐스팅** 

```swift
func someFunc(info: [String: Any]){
 
    // value 값 타입 any 라서 String 인지 캐스팅
    guard let name = info["name"] as? String else {
        return
    }
    // value 값 타입 any 라서 Int 인지 캐스팅, age >= 0 조건 검사
    guard let age = info["age"] as? Int, age >= 0 else {
        return
    }
    print("\(name): \(age)")
}

someFunc(info: ["name":"mina", "age" : "21"]) // age가 string이라 반환 되어버림
someFunc(info: ["name":"mina", "age" : 21]) // mina: 21
```

