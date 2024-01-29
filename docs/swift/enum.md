---
layout: default
title: 9-2. 열거형
parent: Swift
---


# 열거형  
{: .fs-6 .fw-300 }


{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## enum

각 case는 그 자체가 고유의 값이다.

### enum 작성 

```swift
enum 이름 {
   case 이름1
   case 이름2
   case 이름3, 이름4 ...
}
```

## Weekday 라는 이넘 작성해보기

### enum 작성하기

```swift
enum Weekday {
    case mon
    case tue
    case wed, thu, fri
}
```

### enum 접근하기 

```swift
// 1.
var day : Weekday = Weekday.mon
// 2.
var day : Weekday
day = .mon

print(day) 
```


```swift
switch day {
case .mon, .tue, .wed, .thu:
    print("평일")
case .fri:
    print("불금")
}
```

day가 한정된 값(변수에 열거형 케이스 하나만 저장 할 수 있어서) 임을 알기 때문에, 스위치문에서 사용할 수 있다. 


## 원시값 
```swift
enum Num: Int {
    case one = 1
    case two = 2
    case three
}

print("three.rawValue == \(Num.three.rawValue)") // 3
print("three.rawValue == \(Num.three)") // three
```

case 별로 각각 다른 값을 가져야 하기 때문에, 정수의 경우 값을 지정해주지 않으면 1씩 증가한다. 
`rawValue`로 값을 꺼낼 수 있다. 

```swift
// 변수의 값으로 초기화
// rawValue 3에 해당하는 케이스는 "three"
// newThree 라는 변수에 "three" 가 대입 된다.
// 만약, 매칭 되는 케이스가 없을 수 있기에 옵셔널로 선언해줘야한다.
let newThree : Num? = Num(rawValue: 3)


// 확인
if let newThree : Num = Num(rawValue: 3) {
    print("raw value 3 에 해당하는 케이스는 \(newThree)")
} else {
    print("raw value 3 에 해당하는 케이스 없습니다. ")
}
```


## 메소드를 포함한 enum

```swift
enum Weekday {
    case mon
    case tue
    case wed, thu, fri
    
    func printMessage() {
        switch self {
            case .mon, .tue, .wed, .thu:
                print("평일")
            case .fri:
                print("불금")
            }
        }
    }

Weekday.fri.printMessage()
```
