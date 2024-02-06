---
layout: default
title: 색상
parent: swiftUI
nav_order: 3
---


# 색상
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Color 

### Basic 

```swift
Color.red
```

### primary

자동으로 다크 모드 색을 지원한다. 

```swift
Color.secondary
Color.primary
```

### UI color 

애플에서 지원하는 색상 키드이다. 

```swift
Color(UIColor.secondarySystemFill)
```

### Custom color

assets에서 만든 헥사 코드 색상을 사용한다. 

```swift
Color("CustomColor")
```


### Gradient 

**LinearGradient**

```swift
.fill(
   LinearGradient(
        gradient: Gradient(colors: [Color.red, Color.blue]),
        startPoint: .topLeading,
        endPoint: .bottom)
)
```

**RadialGradient**

```swift
.fill(
   RadialGradient(
         gradient: Gradient(colors: [Color.red, Color.yellow]), //색상
         center: .leading, // (시작점)중심점
         startRadius: 5, // 시작 크기
         endRadius: 100) // 퍼짐 크기
)
```

**AngularGradient**

```swift
.fill(
    AngularGradient(
          gradient: Gradient(colors: [Color.yellow, Color.blue]),
          center: .topLeading,
          angle: .degrees(180 + 45))
)
```

