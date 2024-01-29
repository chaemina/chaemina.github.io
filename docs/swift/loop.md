---
layout: default
title: 7. 반복문
parent: Swift
---


# 반복문
{: .no_toc }

조건문과 반복문은 다른 언어들과 동일하게 동작한다. 
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## for ... in


### 1. Array 

```swift
var nums = [1,2,3]

print(nums) //  [1, 2, 3]

for num in nums {
    print(num) // 1 2 3 (줄 바꿈)
}
```

### 2. Dictionary

```swift
let students = ["mina" :21, "hana": 22, "yusun" :23]

print(students) // ["hana": 22, "mina": 21, "yusun": 23]

for (name, age) in students {
    print("\(name)의 나이는 \(age)")  // hana의 나이는 22 ... (줄 바꿈)
}
```

## while

```swift
while nums.count > 1 {
    nums.removeLast()
    // 1. 처음 반복 카운트 3 > 1 : true -> 마지막 원소 3 지워짐
    // 2. 두번째 반복 카운트 2 > 1 : true -> 마지막 원소 2 지워짐
    // 3. 세번째 반복 카운트 1 > 1 : false -> [1] 을 반환
}
```

## repeat while 

```swift
repeat {
    nums.removeLast()
} while nums.count > 0
```
do - while 과 같은 기능을 한다. 


{:.warning}
조건문이나, while문에서의 조건은 반드시 Bool 타입의 값이어야 한다.

