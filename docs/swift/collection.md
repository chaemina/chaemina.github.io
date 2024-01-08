---
layout: default
title: 4. 컬렉션 타입 
parent: Swift
---


# 컬렉션 타입 
{: .no_toc }

swift에서 컬렉션 타입은 지정된 타입의 데이터 묶음을 뜻한다. 
{: .fs-6 .fw-300 }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## Array 
순서가 있는 리스트 컬렉션 

### 1. Array 생성하기 
(1) 변수로 빈 배열 선언하기 

 `var 배열이름 : Array<타입> = Array<타입>( )`

```swift
var firstArray : Array<Int> = Array<Int>()
var secondArray : Array<Int> = [Int]()
var thirdArray : [Int] = [Int]()
var fourthArray : [Int] = []
```

(2) 상수로 값이 있는 배열 선언하기 
```swift
let letArray = [1,2,3]
```

{: .highlight}
상수로 선언된 배열은 `append` `remove` 메소드로 값을 변경 할 수 없다. 

### 2. 배열 관련 메소드 

```swift
firstArray.append(1)
firstArray.append(100)
// firstArray.append("hi") 배열 타입 벗어나서 안됨
```
```swift
firstArray.remove(at: 0) // 0번 인덱스 삭제
firstArray.removeLast() // 마지막 인덱스 삭제
firstArray.removeAll() // 모든 배열 원소 삭제
```

```swift
firstArray.contains(1) // true
firstArray.contains(101) //false
```

```swift
firstArray.count // 원소의 개수
```



## Dictionary 
키와 값의 쌍으로 이루어진 컬렉션 

