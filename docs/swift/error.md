---
layout: default
title: 오류 처리 
parent: Swift
nav_order: 22
---


# 오류 처리 
{: .no_toc }


Swift 에서는 주로 Error 프로토콜과 열거형으로 오류를 표현한다. 
{: .fs-6 .fw-300 }





## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Error 

```swift 
enum 오류 종류 이름: Error {
       case 종류1
       case 종류2
}
```

### 오류 정의 

```swift
enum MyError: Error {
    case errorA
    case errorB(n: Int)
}
```

### 함수에서 오류 처리 
```swift
class Func {
    var num : Int = 100
    var sum : Int = 0
    
    func numSum(n: Int) throws {
        
   // n이 0보다 작을 경우 errorB 호출 
        guard n > 0 else {
            throw MyError.errorB(n: n)
        }
        self.num += sum
        print("합계 \(sum)")
    }
}

var myFunc : Func = Func()
myFunc.numSum(n: -100)
```

 <img src="../../../assets/images/error.png" alt="assert Image" aria-label="assert Image" width="50" height="30">

## try 

오류 발생의 여지가 있는 thorw 함수는 `try`를 사용하고, do-catch 구문을 활용하여 오류를 대비한다. 

```swift
do {
    try myFunc.numSum(n: -100)
} catch MyError.errorA {
    print("오류가 발생했습니다.")
} catch MyError.errorB(let n){
    print("입력이 잘못 되었습니다.")
} // 입력이 잘못 되었습니다. -> 내가 함수에 에러B 만 호출 해서 

```

혹은 스위치문으로 에러 케이스 정리 

```swift
do {
   try myFunc.numSum(n: -100)
} catch {
     switch error {
     case MyError.errorA:
         print("error A 에러 발생")
     case MyError.errorB:
         print("error B 에러 발생")
     default: 
         print("알 수 없는 오류")
     }
}
```

### try?

별도의 오류 처리 결과를 통보 받지 않고, 오류가 발생 했으면 결과 값을 nil로 돌려 받는다. 정상 동작 후에는 옵셔널 타입으로 정상 반환 값을 돌려 받는다. 

### try!

오류가 발생하지 않을 거라고 확신 할 때 사용한다. 오류 발생 시 런타입 오류로 앱이 중지 된다. 



