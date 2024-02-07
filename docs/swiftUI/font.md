---
layout: default
title: 폰트 
parent: Swift UI
nav_order: 1
---


# 폰트 
{: .no_toc }

Swift UI에 관한 모든 개념은 인프런의 [해당강의](https://www.inflearn.com/course/누구나-swiftui-ios16)를 수강하고 작성하였다.
{: .fs-6 .fw-300 }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## font 

### responsive 하게 지정 

`title` `body` `footnote` 등으로 지정하면, 반응형으로 폰트 사이즈가 동작한다. 

<img src="../../../assets/images/font.png" alt="assert Image" aria-label="assert Image" width="600" height="600">

```swift
Text("Hello, World!")
     .font(.title2) // 폰트 사이즈 
     .fontWeight(.light) // 폰트 두께 
     .bold() // 폰트 두께 
     .underline(true, color: Color.indigo) // 밑줄 
     .italic() // 이테릭체 
     .strikethrough(true, color: Color.yellow) //가운데 줄 
     .foregroundColor(.pink) // 폰트 색상 

```


### system으로 크기 지정 

크기를 고정적으로 지정한다. 

```swift
Text("hello world 2".uppercased())
     .font(.system(size: 20, weight: .bold, design: .serif))
```

### 멀티 라인 

```swift
Text("멀티라인 텍스트 정렬입니다. 멀티라인 텍스트 정렬입니다. 멀티라인 텍스트 정렬입니다.")
    .multilineTextAlignment(.trailing)   // leading : 왼쪽 center : 중앙 trailing : 오른쪽
```


<img src="../../../assets/images/font2.png" alt="assert Image" aria-label="assert Image" width="300" height="600">