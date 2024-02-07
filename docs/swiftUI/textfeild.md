---
layout: default
title: 텍스트 필드 
parent: Swift UI
nav_order: 14
---


# 텍스트 필드 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Text Field

 `TextField("placeholder", text: $inputText)`

ios 17은 시뮬레이터에서 키보드로 한글 입력 시 깨짐 현상이 나타난다. (복사 붙여넣기는 가능)

### 유효성 검사 

입력 된 문자열의 상태를 실시간으로 감지하여 간단한 유효성 검사를 실행 할 수 있다. 

```swift
@State var inputText : String = ""

TextField("2글자 이상 입력하세요.", text: $inputText)
```

```swift
func isTextEnough() -> Bool {
        if (inputText.count >= 2){
            return true
        } else {
            return false
        }
    }
```

```swift
Button(action: {
             if isTextEnough() { // 유효성 검사 후 실행 로직
               }}, label: {
                    Text("Submit".uppercased())
                        .background(isTextEnough() ? .blue : .gray) // 색상변화
                }).disabled(!isTextEnough()) // 유효성 검사에 따른 버튼 비활성화 처리
```



긴 글은 [TextEditor](https://developer.apple.com/documentation/swiftui/texteditor)을 사용한다. 