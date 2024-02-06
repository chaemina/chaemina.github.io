---
layout: default
title: 배치 
parent: swiftUI
nav_order: 5
---


# 배치 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 배치 

크기를 상대적으로 어떻게 맞출 지 정한다.

### scaledToFill

종횡비를 유지하면서 부모를 채우기 위해 이 뷰를 확장한다. 


<img src="../../../assets/images/scaled-to-fill.png" alt="assert Image" aria-label="assert Image" width="500" height="500">

### scaledToFIt 

종횡비를 유지 하면서 부모에 맞게 이 뷰를 확장한다. 


<img src="../../../assets/images/scaled-to-fit.png" alt="assert Image" aria-label="assert Image" width="500" height="500">

## Frame 

```swift 
 .frame(width: height: alignment: )
```

1. alignment의 default 값은 center 
1. 스크린 전체 사이즈는 `UIScreen.main.bounds.height` 혹은 `UIScreen.main.bounds.width`
1. 최대한으로 늘릴 때 `maxWidth:.infinity, maxHeight: .infinity`


```swift
VStack(spacing:20) {
            Text("hello world")
                .font(.title)
                .background(Color.green)
            // 프레임의 크기를 확인 하기 위해
                .frame(width: 200, height: 200, alignment: .center)
                .background(Color.red)
        }
```

<img src="../../../assets/images/frame.png" alt="assert Image" aria-label="assert Image" width="500" height="500">


프레임은 요소의 부모 틀과 같아서, 프레임 지정 후 색상을 적용하면 요소가 배치 된 기준을 확인 할 수 있다. 

