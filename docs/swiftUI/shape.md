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

원형 `Circle()` <br/>
타원형 `Ellipse()` <br/>
캡슐형 `Capsule(style: .continuous || .circular)` <br/>
직사각형 `Rectangle()` <br/>
둥근 직사각형 `RoundedRectangle(cornerRadius: 20)` 

### 색상 

```swift
.fill(Color.yellow) //우선순위
.foregroundColor(.pink)
```

### 테두리 

```swift
.stroke(Color.orange, lineWidth: 5)
```

{: .warning}
stroke와 foregroundColor 동시에 사용 불가

```swift
.stroke(Color.purple, style: StrokeStyle(lineWidth:20, lineCap: .round, dash: [30]))
```

{: .warning}
StrokeStyle과 fill 동시에 사용 불가 

### 변형 

```swift
.trim(from: 0.2 to: 1)
```

{: .warning}
trim과 fill, foregroundColor 동시에 사용 불가 <br/> trim과 stroke 동시에 사용하려면, trim을 먼저 선언해야 한다. 

### 크기 

```swift
.frame(width: 200, height: 100, alignment: .center) 
```


{: .note-title }
> **주의**
>
> 원형은 가로 세로 사이즈 같게 지정해야한다.  <br/> 그렇지 않은 경우, 더 작은 크기의 사이즈로 적용된다. 



