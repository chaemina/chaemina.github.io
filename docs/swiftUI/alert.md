---
layout: default
title: Alert
parent: Swift UI
nav_order: 13
---


# Alert
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Alert Basic

 `.alert(isPresent: 발생여부, content: 어떤 Alert)`

```swift
@State var showAlert :Bool = false 


Button (action: { 
     showAlert.toggle()
     } label : {
        Text("Alert 1")})
    .alert(isPresented; $showAlert, content: {Alert(title: Text("기본 Alert"))})
```

타이틀만 가지는 Alert을 리턴한다. 

## Alert Custom 

content에서 Alert을 커스텀 한 함수를 호출한다. 

### 삭제, 취소 버튼 

```swift
func getAlert() -> Alert {
        return Alert(
            title: , message: ,
            primaryButton: , 
            secondaryButton:
        )}
```

반환 타입으로 title, 1번 버튼, 2번 버튼을 가지는 Alert 구조체를 리턴한다. 

**삭제 버튼**

`.destructive(label: Text("삭제"), action: 삭제버튼 클릭시 발생)`

**취소 버튼**

`.cancel(Text("취소"))`

취소 버튼의 동작은 지원하지만, 삭제 버튼의 동작은 정의 해줘야 한다. <br/>



### enum 활용 

enum의 케이스를 스위치 구문으로 하여 Alert을 반환한다. 

```swift
enum AlertCase {
      case success
      case error
}
```
Alert의 케이스를 enum으로 정의한다. 


```swift
func getAlert() -> Alert {
        switch alertType {
        case .success:
            return Alert(
                title: Text("성공"),
                message: Text("성공 메세지"),
                dismissButton: .default(Text("OK")) {
                    backgroundColor = .green
                }
            )
        case .error:
            return Alert(
                title: Text("실패"),
                message: Text("실패 메세지"),
                dismissButton: .default(Text("OK")) {
                    backgroundColor = .red
                }
            )
        case nil:
            return Alert(
                title: Text("원인 모르는 에러 발생"),
                message: Text("원인을 알 수 없는 에러입니다."),
                dismissButton: .default(Text("OK")) {
                    backgroundColor = .purple
                }
            )
        }
    }

```

switch 구문으로 케이스 별 반환 될 Alert 구조체를 작성한다. 


```swift
HStack(spacing:10) {
          Button(action: {
                 alertType = .error
             }, label: {
                 Text("Alert 실패 시")
             })
             
           Button(action: {
                  alertType = .success
             }, label: {
                 Text("Alert 성공 시")
             })       
         }.alert(isPresented: $showAlert, content: { getAlert() })
```

Type에 맞게 Alert이 호출 된다. 