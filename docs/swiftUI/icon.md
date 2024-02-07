---
layout: default
title: 아이콘 
parent: Swift UI
nav_order: 4
---


# 아이콘 
{: .no_toc }


애플에서는 [SF Symbols](https://developer.apple.com/sf-symbols/)을 xcode에서 기본 제공 하고 있다.
{: .fs-6 .fw-300 }



## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Icon

SF Symbols에서 아이콘의 이름을 복사하여 사용한다. 

```swift
Image(systemName: "square.and.arrow.up")
```

### 속성 

1. `.resizeable()` 사이즈 변경 가능하도록 설정 
1. `.renderingMode(.original)` 고유 컬러 적용 (커스텀 불가) 
1. `foregroundColor` fill 메소드 적용 불가 

