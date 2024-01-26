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
1. 변수로 빈 배열 선언하기 

 `var 배열이름 : Array<타입> = Array<타입>( )`

```swift
var firstArray : Array<Int> = Array<Int>()
var secondArray : Array<Int> = [Int]()
var thirdArray : [Int] = [Int]()
var fourthArray : [Int] = []
```

1. 상수로 값이 있는 배열 선언하기 
```swift
let letArray = [1,2,3]
```

### 2. 배열 관련 메소드 

1. 배열 값 삽입하기 
```swift
firstArray.append(1)
firstArray.append(100)
// firstArray.append("hi") 배열 타입 벗어나서 안됨
```

1. 배열 값 제거하기
```swift
firstArray.remove(at: 0) // 0번 인덱스 삭제
firstArray.removeLast() // 마지막 인덱스 삭제
firstArray.removeAll() // 모든 배열 원소 삭제
```

1. 그 외 메소드 
```swift
firstArray.contains(1) // true
firstArray.contains(101) //false
```

```swift
firstArray.count // 원소의 개수
```



## Dictionary 
키와 값의 쌍으로 이루어진 컬렉션 

### 1. Dictionary 생성하기 
1. 변수로 빈 객체 선언하기 

 `var 객체이름 : Dictionary<key 타입, value 타입> = [key 타입:value 타입]( )`

```swift
var firstDictionary : Dictionary<String, Any> = [String:Any]()
var secondDictionary : [String:Any] = [:]
```

1. 상수로 값이 있는 객체 선언하기 
```swift
var thirdDictionary : [String:Any] = ["name":"mina", "age": 21]
```

### 2. 객체 값 변경하기 

1. 객체 값 삽입하기 
```swift
firstDictionary["name"] = "mina"
firstDictionary["age"] = 21
// ["age": 21, "name": "mina"]
```

1. 객체 값 변경하기 
```swift
firstDictionary["age"] = 23
//["age": 23, "name": "mina"]
```

1. 객체 값 제거하기 
```swift
firstDictionary.removeValue(forKey: "age")
firstDictionary["age"] = nil
// 같은 결과 ["name": "mina"]
```



## Set
순서가 없고 멤버가 유일한 컬렉션 

### 1. Set 생성하기 
1. 변수로 빈 set 선언하기

 `var set이름 : Set<type> = Set<type>( )`

 ```swift
 var setA : Set<Int> = Set<Int>()
 ```

1. 상수로 값이 있는 set 선언하기 
```swift
let setB : Set<Int> = [1,2,3,4]
```

### 2. Set 관련 메소드 

1. Set 값 삽입하기 
```swift
setA.insert(1)  // [1]
setA.insert(100)  // [1, 100]
setA.insert(1)  // [1, 100] set은 동일 값 1개 이상 넣지 않음
```

1. Set 값 제거하기 
```swift
setA.remove(100) // [1]
setA.removeFirst() // [] 첫번째 원소 삭제
```

1. 결합 
```swift
let setC : Set<Int> = [4,5,6,7,8]

let union : Set<Int> = setB.union(setC) //[5, 6, 3, 8, 7, 4, 2, 1] 합집합

let sortedUnion : [Int] = union.sorted() //[1, 2, 3, 4, 5, 6, 7, 8] 정렬

let intersection : Set<Int> = setB.intersection(setC) // [4] 교집합

let subtracting : Set<Int> = setB.subtracting(setC) //  [3, 1, 2] 차집합
```

1. 그 외 메소드  
```swift
setB.contains(1) // true
setB.contains(10) //false
```

```swift
setA.count
```



{:.warning}
상수로 선언된 Array, Dictionary, Set의 값은 변경 할 수 없다. 
