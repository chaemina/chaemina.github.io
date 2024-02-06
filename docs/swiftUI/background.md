---
layout: default
title: 백그라운드와 오버레이 
parent: swiftUI
nav_order: 6
---


# 백그라운드와 오버레이 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 요소의 프레임 

해당 요소의 프레임이 앞으로 갈지, 뒤로 갈지 결정한다. 

### background

```swift
Circle()
    .fill(Color.yellow)
    .frame(width: 100, height: 100)
    .background(Color.green)
```

<img src="../../../assets/images/background.png" alt="assert Image" aria-label="assert Image" width="500" height="500">

### overlay 

```swift
Circle()
    .fill(Color.yellow)
    .frame(width: 100, height: 100)
   .overlay(Color.green)
```

<img src="../../../assets/images/overlay.png" alt="assert Image" aria-label="assert Image" width="500" height="500">


## 다른 요소 

다른 요소가 해당 요소의 앞에 나타날지, 뒤에 나타날지 결정한다. 

<img src="../../../assets/images/background-overlay.png" alt="assert Image" aria-label="assert Image" width="500" height="500">

위의 그림과 같이 배치하려면, 

### background 

```swift
Circle()
    .fill(Color.blue)
    .frame(width: 100, height: 100)
    .background(
          Rectangle()
               .frame(width: 200, height: 200)
             ,alignment: .leading )
```

### overlay 

```swift
Rectangle()
   .frame(width: 200, height: 200)
   .overlay(
   // 오버레이 안에 원을 그린다. 
      Circle()
           .fill(Color.blue)
           .frame(width:100 , height: 100)
        ,alignment: .leading  ) 
```

{: .highlight}
오버레이에서 정렬은 프레임 밖에서 쉼표로 작성한다. 


## ZStack과 ovarlay 중 어느걸로 쌓을까? 

[ZStack](https://chaemina.github.io/docs/swiftUI/stack)도 오버레이와 같이 요소를 쌓는 동작을 한다. <br/>
코드가 단순한 경우 오버레이로 작성하고, 복잡한 경우 ZStack으로 작성하는 것이 좋다. 

### 비교코드 

**ZStack**

```swift
ZStack(alignment: .topLeading){
            Rectangle()
                .fill(Color.blue)
                .frame(width: 200, height: 100)
            Circle()
                .fill(Color.red)
                .frame(width:100)
        }
```

**overlay**

```swift
 Rectangle()
            .fill(Color.blue)
            .frame(width: 200, height: 100)
            .overlay(
                Circle()
                    .fill(Color.red)
                    .frame(width: 100)
                ,alignment: .topLeading
            )
```
