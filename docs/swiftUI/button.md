---
layout: default
title: 버튼과 프로퍼티 래퍼 
parent: Swift UI
nav_order: 9
---


# 버튼과 프로퍼티 래퍼 
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Button

```swift
Button(action: {}, label: {})
```


라벨에 해당하는 부분을 클릭하면, action 로직이 실행된다. 


## Property wrapper

`@` 특정 프로퍼티의 저장 방식을 관리하거나, 프로퍼티에 대한 접근 방식을 커스터마이징 하기 위해 사용되는 기능이다. 프로퍼티 래퍼를 사용하면 
보일러 플레이트 코드를 줄이고 코드 재사용성을 높일 수 있다. 

### @State 

변수가 변경 될 때, 뷰에서도 업데이트 되면서 값을 변경한다. (React의 useState 처럼 상태관리)

```swift 
@State var mainTitle : String = "아직 버튼 안눌림"


var body: some View {
        VStack(spacing: 20){
           
            Text(mainTitle)
                .font(.title)
            
            Button(action: {
                // 변수 mainTitle 의 컨텐츠 변화 시킴
                self.mainTitle = "기본 버튼 눌림"
            } , label: {
                Text("기본 버튼") })
        }
}
```

"기본 버튼" 이라는 라벨의 버튼을 클릭하면, mainTitle의 내용을 변화 시키는 동작이 실행된다. 


### @Binding 

뷰를 분리 했을 때, `@State`를 하위뷰(서브뷰)에서 사용하기 위한 래퍼이다. (전역 상태 느낌) <br/>
하위 뷰의 특정 프로퍼티 값이 변경 되면, 상위 뷰의 특정 프로퍼티 값도 변경된다. (양방향) <br/>

**상위 뷰**

```swift
struct BindingBasic: View {
    
    @State var backgroundColor : Color = Color.green
    @State var title : String = "Binding Basic View"
    
    var body: some View {
        
        ZStack {
            //background
            backgroundColor
                .ignoresSafeArea()
            
            //content
            VStack {
                Text(title)
                
                // button, 하위 뷰는 상위 뷰에 나타날 버튼의 UI
                BindingChild(backgroundColor: $backgroundColor, title: $title)
            }
        }
    }
}
```

프로퍼티 래퍼 변수를 인자로 넘겨줄 때는, `$`를 붙여야 한다. 


**하위 뷰**


```swift
struct BindingChild: View {
    
    @State var buttonColor : Color = Color.blue
    @Binding var backgroundColor : Color
    @Binding var title : String

    
    var body: some View {
        Button(action: {
            backgroundColor = Color.orange
            buttonColor = Color.pink
            title = "Biding Child View"
        }, label: {
            Text("Child View 이동")
                .foregroundColor(.white)
                .padding()
                .padding(.horizontal)
                .background(buttonColor)
                .cornerRadius(10)
        })
    }
}
```

부모 뷰에서 넘겨 준 `@State` 인자를 바인딩 할때는 `@Binding` 으로 선언한다. 

## Toggle

```swift
  Toggle(isOn: ){ title }
 ``` 

Swift UI에서는 토글 형태의 버튼을 지원한다. 

```swift
@State var isToggleOn : Bool = false

    HStack {
       Text("로그인 상태")
       Text(isToggleOn ? "로그인" : "로그아웃")
           .foregroundColor(isToggleOn ? .blue : .red)
        }
     Toggle(isOn: $isToggleOn){ Text("로그인 상태 선택") }
```

