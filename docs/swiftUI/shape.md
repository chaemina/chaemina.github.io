---
layout: default
title: 도형
parent: Swift UI
nav_order: 2
---


# 도형 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Shape 

```swift
Circle() // 원형 
Ellipse() // 타원형
Capsule(style: .continuous || .circular) // 캡슐형 
Rectangle() // 직사각형 
RoundedRectangle(cornerRadius: 20) // 둥근 직사각형 
```


### 색상 

```swift
.fill(Color.yellow) //우선순위
.foregroundColor(.pink)
```

### 테두리 

```swift
.stroke(Color.orange, lineWidth: 5)
```

`stroke`은 `foregroundColor`와 동시에 사용 할 수 없다. 

```swift
.stroke(Color.purple, style: StrokeStyle(lineWidth:20, lineCap: .round, dash: [30]))
```

`StrokeStyle`은 `fill`과 동시에 사용 할 수 없다. 

### 변형 

```swift
.trim(from: 0.2 to: 1)
```

1. `trim`은 `fill`이나 `foregroundColor`과 동시에 사용할 수 없다. 
1. `trim`과 `stroke`을 동시에 사용하려면, `trim`을 먼저 선언해야 한다. 

### 크기 

```swift
.frame(width: 200, height: 100, alignment: .center) 
```


{: .note-title }
> **주의**
>
> 원형은 가로와 세로 사이즈를 같게 지정해야한다.  <br/> 그렇지 않은 경우, 더 작은 사이즈의 값으로 적용된다. 



