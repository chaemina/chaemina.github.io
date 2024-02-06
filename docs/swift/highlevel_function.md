---
layout: default
title: 고차 함수 
parent: Swift
nav_order: 23
---


# 고차 함수 
{: .no_toc }


전달 인자로 함수를 전달 받거나, 함수의 실행 결과를 함수로 반환하는 함수이다. 
{: .fs-6 .fw-300 }





## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## map 

컨테이너 내부의 기존 데이터를 변형하여 새로운 컨테이너를 생성한다. 

```swift
let numbers : [Int] = [0,1,2,3,4]

var nums : [Int]
var strings : [String]

// number 의 각 요소 출력 
nums = numbers.map({(num: Int) -> Int in return num})

// number 의 각 요소를 문자열로 변환, 새로운 배열로 출력 
strings = numbers.map({(num: Int) -> String in return  "\(num)" })

print(nums) //[0, 1, 2, 3, 4]
print(strings) // ["0", "1", "2", "3", "4"]
```

클로저 구문 축약 가능 

```swift
nums = numbers.map({$0})
strings = numbers.map({"\($0)"})

// 결과 동일 
print(nums) //[0, 1, 2, 3, 4]
print(strings) // ["0", "1", "2", "3", "4"]
```


## filter 

컨테이너 내부의 값을 걸러서 새로운 컨테이너로 추출한다. 

```swift
let numbers : [Int] = [0,1,2,3,4]

let evenNums : [Int] = numbers.filter {
     // 리턴 타입이 불리언 
    (num: Int) -> Bool in
    return num % 2 == 0
}

print(evenNums)
```

{: .highlight}
반복문을 사용하면 필터링 되는 값을 변수로 선언해줘야 하는데, filter 함수 사용하는 경우는 상수로도 가능하다. 

클로저 구문 축약 가능 

```swift
let evenNums: [Int] = numbers.filter{$0 % 2 == 0}

print(evenNums)
```


## reduce

컨테이너 내부의 콘텐츠를 하나로 통합한다. 

```swift
let numbers : [Int] = [2,8,15]

// 초기값이 0이고 numbers 내부의 모든 값을 더한다.
let sum : Int = numbers.reduce(0,{
    (first: Int, second: Int) -> Int in
    return first+second })

print(sum) //25
```

클로저 구문 축약 가능 

```swift
let sum : Int = numbers.reduce(0, { $0 + $1})
 
print(sum)
```

곱셈 연산의 경우, 초기값을 1로 지정해야 한다. 
{: .warning}