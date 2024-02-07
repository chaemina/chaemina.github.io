---
layout: default
title: 스택과 패딩 
parent: Swift UI
nav_order: 7
---


# 스택과 패딩 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Stack 

요소들을 쌓는 방향을 결정한다. 


### VStack 
Vertical stack 요소를 세로로 쌓는다. 

### HStavk 
Horizontal stack 요소를 가로로 쌓는다. 

### ZStavk 
z-index stack 요소를 다른 요소의 위로 쌓는다. (우선순위)


## 배경 색상 지정하기 

ZStack을 활용하여 배경 색상을 지정할 수 있다. 먼저 작성한 코드가 우선 순위가 낮기 때문에 최상단에 작성한다. <br/>
`ignoresSafeArea()` 메소드는 뷰의 모서리를 채워준다. 


```swift
ZStack(){
    Color("BackgroundColor").ignoresSafeArea()
}
```


## Padding 

요소의 여백을 설정한다. swift에서는 margin이 없고, 해당 기능을 padding으로 구현해야한다. 

<img src="../../../assets/images/padding0.png" alt="padding Image" aria-label="padding Image" width="300" height="500">

위의 그림에 다음과 같이 순서대로 padding을 적용 한다. 

```swift
.padding()
.padding(.vertical, 30)
.background(Color.orange
            .cornerRadius(10))
.padding()

```

**1번 padding**

<img src="../../../assets/images/padding1.png" alt="padding Image" aria-label="padding Image" width="300" height="500">

해당 요소의 프레임 상하 좌우에 패딩값이 적용된다. 

**2번 padding**

<img src="../../../assets/images/padding2.png" alt="padding Image" aria-label="padding Image" width="300" height="500">

상하 패딩값이 적용된다. 

**3번 padding**

<img src="../../../assets/images/padding3.png" alt="padding Image" aria-label="padding Image" width="300" height="500">

background 이후 적용된 패딩은 마진의 역할을 한다. 

