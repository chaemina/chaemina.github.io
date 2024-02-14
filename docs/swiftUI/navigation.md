---
layout: default
title: 네비게이션과 시트 
parent: Swift UI
nav_order: 11
---


# 네비게이션과 시트 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Navigation View 

뷰 간의 라우터를 처리한다. Navigation을 사용 하기 위해선, 최 상단에 NavigationView를 선언해야 한다. 

```swift
var body : some View {
    NavigationView {
    } // : navigation view 
}
```

### Navigation View 속성 

1. `.navigationTitle("페이지 제목")`  상단의 페이지 제목 
1. `.navigationBarItems(leading: EditButton(), trailing: )` 상단의 좌우 아이템 설정(수정 버튼 지원)
1. `.navigationBarTitleDisplayMode(.inline)`  제목 스타일 
    -  `.automatic` 
    -  `.inline` 중앙에 작게 
    -  `.large` 앞쪽에 크게

### Navigation Link 연결 

Navigation Link로 연결하여, 첫 번째 뷰에서 두 번째 뷰로 이동 할 수 있다. 

```swift
// 첫 번째 뷰 
        NavigationView{
            
            NavigationLink {
                // 이동 할 뷰
                SecondNavigation() // 두 번째 뷰 
            } label: {
               // 버튼 라벨
                Text("Second view 로 이동")
            } 
        }
```

{: .highlight}
두 번째 뷰에서 다시 세 번째 뷰로 이동 할 때에는, Navigation View 없이 Navigaion Link만 작성하면 된다. 


## Navigation Stack

Navigation Stack은 SwiftUI에 WWDC 22에서 도입되어, Navigation View를 대체 하기 위해 생겼다. <br/>
Navigation View는 스택 기반의 네비게이션을 구현하는 전통적인 방식을 제공하는 반면, Navigation Stack은 데이터 기반 네비게이션을 쉽게 구현 할 수 있도록 설계 되었다. 

```swift
// 첫 번쨰 뷰 
@State private var showDetails = false

NavigationStack {
    VStack {

        Button("Second view 로 이동") {
            showDetails = true
        }
    }
    .navigationDestination(isPresented: $showDetails) {
        // 이동 할 뷰 
         SecondNavigation()  // 두 번째 뷰 
    }
    .navigationTitle("Navigation Stack")
}
```

[navigationDestination](https://developer.apple.com/documentation/swiftui/view/navigationdestination(ispresented:destination:))수정자를 사용하여 이동을 도울 수 있다. 


## Sheet 

### sheet 

 `.sheet(isPresented : 시트 보여지는 조건 ) { 보여질 내용 }`

현재 뷰에서 약 90% 부분 정도 오버레이 되는 뷰이다. sheet에는 기본적으로 애니메이션 효과가 탑재 되어 있다. 


```swift
@State var showSheet : Bool = false
              
     Button {
           showSheet.toggle()
      } label : {
           Text("Button")
      }
   
     .sheet(isPresented: $showSheet) {
        Sheet()   // 보여질 내용 
    }
```


### fullScreenCover

 `.fullScreenCover(isPresented : 시트 보여지는 조건 ) { 보여질 내용 }`
 
 현재 뷰에서 전체 부분 오버레이 되는 뷰이다.

```swift
@State var showSheet : Bool = false
              
     Button {
           showSheet.toggle()
      } label : {
           Text("Button")
      }
   
     .fullScreenCover(isPresented: $showSheet) {
        Sheet()   // 보여질 내용 
    }
```


### sheet 닫기 

Sheet애서 닫는 버튼을 만들고 싶으면, 환경변수 `@Environment`로 presentaionMode 선언 후 wrappedValue.dismiss() 를 호출한다. 

```swift
    @Environment(\.presentationMode) var presentaionMode

     Button {
        // sheet 닫기
        presentaionMode.wrappedValue.dismiss()
     } label: {
        Image(systemName: "xmark")
   }
```



{: .note-title }
> **중요**
>
> sheet는 스크롤을 내려서 시트를 닫을 수 있는 반면, fullScreenCover은 닫을 수 없기 때문에 닫기 버튼이 필요하다. 

### sheet에서 navigatio 사용 

sheet안에서 navigation link 버튼은 disable 되어 사용 할 수 없다. 

```swift
struct NavigationWithSheet: View {
     
    @State private var showSheet : Bool = false
    @State private var navigate : Bool = false

        var body: some View {
        NavigationStack {
            VStack {
                Button("show Sheet") {
                    showSheet.toggle()
                }
            }
            .navigationTitle("naviagation with sheet")
            .sheet(isPresented: $showSheet, content: {
                Button("Button Link"){
                        showSheet = false
                        navigate = true
                    }})
            .navigationDestination(isPresented: $navigate) {
                Text("Destination from Button")
            }
        } // : navigation stack
```

navigation destination의 ispresented 속성을 사용 하여 해결 한다. 