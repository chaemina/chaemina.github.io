---
layout: default
title: 리스트
parent: Swift UI
nav_order: 12
---


# 리스트 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## List 

 `List { Section { content , 속성 } header: { title } }`

Section 내부에 content와 속성을 모두 작성한다. 


## List content 

주로 배열을 ForEach 문으로 반복하여 나열할 때 사용된다. 


```swift
 List  {
    Section { 
       ForEach(fruits, id: \.self){
            Text($0) }
      } header: {
            Text("과일 리스트")
   } // : section 1
}
```


### List 속성 


```swift 
.onDelete(perform: delete)

func delete(indexSet: IndexSet) {
        fruits.remove(atOffsets: indexSet) }
```

```swift
.onMove(perform: move)

func move(indexSet: IndexSet, newOffset: Int) {
        fruits.move(fromOffsets: indexSet, toOffset: newOffset) }
```

```swift
.listRowBackground(Color.blue) // 배경색 
```

{: .highlight}
💡 NavigationView 안에서 선언된 리스트는 네비게이션 바 아이템으로 컨텐츠 수정이 가능하다. 