---
layout: default
title: 애니메이션 
parent: Swift UI
nav_order: 10
---


# 애니메이션 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## withAnimation

 `withAnimation(animation: Animation)`


```swift
Button(action: {
    withAnimation(.default) {
          isAnimated.toggle() 
       }
    }, label: {
    Text("Button") })
```

버튼 클릭 시, default 속성의 애니메이션 효과와 isAnimated(Bool 타입) 변수값 토클이 동작한다.

### 속성

| 속성        | 기능        | 
|:-------------|:------------------|
| `.default`   | 기본 | 
| `.delay(n)`  | n초 뒤에 시작  | 
| `.repeatForever()`|  n회 반복 | 
| `.spring(response: ,dampingFraction: ,blendDuration: )`   |    - response : 단일 진동을 완료하는 데 걸리는 시간 
   - dampingFraction : 얼마나 빠르게 스프링을 정지 하는지 (0-1 사이의 값)
   - blendDuration : 다른 애니메이션 간의 전환 길이 제어  | 
|`.linear(duration: )`   | 처음부터 끝까지 속도 일정   | 
|`.easeIn(duration: )`|  처음엔 느리고 끝에 빨라짐 |
| `.easeOut(duration: )` | 처음엔 빠르고 끝에 느려짐  |
| `.easeInOut(duration: )`|  처음과 끝에 느리고 중간에 빨라짐 | 


### 효과

| 효과        | 기능        | 
|:-------------|:------------------|
|`.rotationEffect(Angle(degree: ))` | 회전효과 |
| `.offset()` | 이동효과 |
| `.transition(.move(edge: .bottom))` | 단 방향 이동 |
| `.transition(.opacity)` | 투명도 조정 |
| `.transition(.scale)` | 크기 조절 |
| `.transition(.asymmetric)` | 비대칭 방향 이동 |

## animation 속성 

withAnimation 대신, animation 속성을 사용 할 수 있다. 단, ios 15 이후로는 animation 속성 사용 시 value 값을 명시해야한다. 

```swift
VStack{
   Button(action: {
        isAnimated.toggle()
       }, label: {
        Text("Button")  })}
        
    Spacer()
        
    RoundedRectangle(cornerRadius: isAnimated ? 50 : 0)
            .fill(isAnimated ? Color.red : Color.green)
            .frame(width: isAnimated ? 100 : 300,
                   height: isAnimated ? 100 : 300)
            .rotationEffect(Angle(degrees: isAnimated ? 360 : 0))
            .offset(y: isAnimated ? 300 : 0)
            .animation(.default, value: isAnimated)
```


