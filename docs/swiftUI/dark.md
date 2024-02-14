---
layout: default
title: 다크 모드 
parent: Swift UI
nav_order: 16
---


# 다크 모드 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Dark mode 

다크 모드 일 때 색을 변환 시키기 위한 방법 3가지를 설명한다. 

### primary and secondary 

primary와 secondary 색상을 사용하면 자동으로 다크 모드 일 때 색이 변환된다. 

```swift
 Text("primary 색상")
    .foregroundColor(.primary)
 Text("secondary 색상")
    .foregroundColor(.secondary)
```

### assets

assets에서 라이트 / 다크 모드 색을 설정하여 사용한다. 

```swift
Text("Assets에서 Adaptive 색 설정")
    .foregroundColor(Color("Adaptive"))
```

### 환경 변수 

환경 변수 `colorScheme` 를 사용하여 다크 모드를 지원한다. 

```swift
@Environment(\.colorScheme) var colorScheme

Text("환경 변수 사용해서 Adaptive 색 설정")
    .foregroundColor(colorScheme == .light ? .black : .white)
```


