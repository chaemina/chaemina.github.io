---
layout: default
title: ForEach
parent: Swift UI
nav_order: 8
---


# ForEach
{: .no_toc }


컬렉션 데이터를 기반으로 뷰를 계산하는 구조체이다. 
{: .fs-6 .fw-300 }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## ForEach

다른 반복문과 달리 ForEach 자체가 일종의 뷰 컨테이너 처럼 작용한다. 

```swift
// 0부터 9까지 반복
 ForEach(0..<10) { index in
     HStack {
        Text("index : \(index)")
    } 
 }

```

1. 범위는 Range<Int> 만 지원한다. 
1. 0..<10 같은 open range<Int>는 가능하지만, 0...10 같은 ClosedRange<Int>는 불가능하다.

{: .note-title }
> **주의**
>
> ForEach가 요구 하는 데이터는 반드시 RandomAccessCollection


### RandomAccessCollection

Swift에서 효율적인 랜덤 접근 인덱스 순회를 지원하는 컬렉션이다. 인덱스 간의 거리 측정이나 인덱스를 임의의 거리 만큼 이동하는 연산을 O(1) 시간안에 
수행 한다. ForEach 구조체가 랜덤 액세스 컬렉션을 요구하는 이유는, ForEach가 컬렉션 내 각 요소에 대한 반복 작업을 수행할 때 빠른 인덱스 계산과 접근이 가능한 컬렉션을 필요로 하기 때문이다. <br/> 
대표적인 예시로는 Array가 있으며 반면에 Dictionary나 Set과 같은 컬렉션은 속하지 않는다. <br/>


**Array, Dictionary, Set(배열, 딕셔너리, 세트)**

- Array (배열): 친구들과 함께하는 여행 계획을 생각해보지. 여행 일정을 순서대로 나열한 목록이 바로 배열(Array)과 같다. 예를 들어, 첫 번째 날은 서울, 두 번째 날은 부산, 세 번째 날은 제주도로 가는 일정이 있다면, 이를 [서울, 부산, 제주도]와 같이 배열로 표현할 수 있다. <br/>
- Dictionary (딕셔너리): 학교에서 학생들의 이름과 학번을 연결해야 한다고 생각해보자. 이때, 학생의 이름이 키(Key)가 되고, 학번이 값(Value)이 된다. 예를 들어, "홍길동": "20220001", "이순신": "20220002"와 같이 이름과 학번을 연결하는 것이 딕셔너리(Dictionary)이다.
- Set (세트): 친구들과 바비큐 파티를 할 때 가져갈 재료 목록을 셍긱헤보자. 소고기, 돼지고기, 닭고기, 채소 등이 있지만, 같은 재료를 두 번 이상 적지 않는다. 이처럼 중복 없이 유일한 값들의 집합을 세트(Set)라고 한다. <br/>

그러니까 아래와 같은 data 배열은 ForEach 구문을 돌 수 있지만, 

```swift
var data : [String] = ["hi", "hello", "hello world"]
```

age 딕셔너리는 ForEach 구문을 돌 수 없다. 

```swift
var ages: [String: Int] = ["John Doe": 30, "Jane Doe": 28]
```


[참조](https://swiftdoc.org/v5.1/protocol/randomaccesscollection/)


### Identifiable 

 `ForEach(array, id: \.self)`


```swift
var data : [String] = ["hi", "hello", "hello world"]

// data의 길이 만큼 반복
    ForEach(data, id: \.self) { item in
          Text(item)}

// for in 구문은 축약 
ForEach(data, id: \.self) {Text($0)}

```


한 배열에 같은 값의 요소가 있다면, 메모리 주소가 다르더라도 구별이 어렵기 때문에 값을 식별하는 id가 필요하다. <br/>
구조체의 경우는 Identifiable 프로토콜을 준수하도록 하고, UUID 타입의 id 속성을 준다. <br/>
이때 구조체와 딕셔너리의 차이가 뭔지 궁금해졌다. (둘다 키- 값의 쌍 아닌가?)


**struct, class (구조체, 클래스)**

- Struct (구조체): 신분증을 예로 들 수 있다. 신분증에는 이름, 생년월일, 주소 등의 정보가 들어 있다. 이러한 정보들을 하나의 단위로 묶어서 관리하는 것이 구조체(Struct)와 유사하다. 각 신분증은 복사할 때마다 독립적인 정보를 담게 된다.
- Class (클래스): 도서관의 도서 대여 시스템을 생각해보자. 하나의 책 정보(제목, 저자, 출판사)를 기반으로 여러 사람이 같은 책을 대여할 수 있다. 이때, 책 정보를 변경하면 대여한 모든 사람에게 영향을 준다. 이처럼 여러 곳에서 공유되고 변경사항이 모두에게 적용되는 특성을 가진 것이 클래스(Class)이다.


{: .highlight}
**Array, Dictionary, Set**은 데이터의 집합을 어떻게 저장하고 관리하는지에 대한 방법 <br/> **Struct, Class**는 데이터의 구조와 관리 방법을 정의하는 틀

이래도 이해가 잘 안된다면, 예시를 봐보자. 

```swift
struct Person {
    var name: String
    var age: Int
    var address: String
}
```

위의 구조체는 Person이라는 데이터의 틀을 가지고 있다. 이 틀을 어떻게 저장하고 관리할지는 다른 차원의 문제이다. 

```swift
var ages: [String: Int] = ["John Doe": 30, "Jane Doe": 28]
```

반면, 딕셔너리는 이미 키와 값을 쌍으로 가지고 있는 데이터 집합인것이다. 




