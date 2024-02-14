---
layout: default
title: ETC
parent: Swift UI
nav_order: 18
---


# ETC
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## AppStorage

app을 나가도 데이터가 저장되어 있도록 한다. 

```swift
@AppStorage("name") var storageName: String?

            VStack(spacing:10) {
                
                Text("Storage 로 저장")
                Text(storageName ?? "당신의 이름은 무엇인가요?")
                
                Button(action: {
                    storageName = "jacob"
                }, label: {
                    Text("이름 불러오기")
                })
                
                Button(action: {
                    storageName = "당신의 이름은 무엇인가요?"
                }, label: {
                    Text("이름 지우기")
                })
            }
```

## 인터넷 이미지 가져오기 

```swift
AsyncImage(url : URL(string: "url 주소")) 
       .frame(width:200, height:200)
```

## icon 변형 

```swift
symbolVariant(.fill)
```

## view that fit

view의 사이즈를 측정하여 가로 / 세로 모드 전환 

```swift
ViewThatFits(in: .horizontal) {
    RoundedRectangle(cornerRadius: 15)
        .fill(.pink.opacity(0.7))
        .overlay{
            Text("가로 모드")
        }
        .frame(width: 700, height: 75)
                
    RoundedRectangle(cornerRadius: 15)
        .fill(.orange.opacity(0.7))
        .overlay{
            Text("세로 모드")
        }
        .frame(width: 350, height: 75)
}
```

