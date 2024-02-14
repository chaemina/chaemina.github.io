---
layout: default
title: MVVM 
parent: Swift UI
nav_order: 17
---


# MVVM
{: .no_toc }

Swift UI로 프로젝트를 만들기 위해서는 MVVM 구조로 디렉토리를 구성한다. 
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## MVVM

- **Model**  앱의 데이터와 비즈니스 로직을 캡슐화, 뷰와 독립적이다. `struct`
- **View Model**  Model과 View 사이의 중재자로, 로직을 정의한다. 뷰에는 데이터를 제공하고 모델에는 업데이트를 요청한다. `class`
- **View**  앱 화면에 시각적 요소들로 인터페이스를 정의한다. `class`

```markdown
-project
| - Model
| - ViewModel
| - View
```

[참조](https://42kchoi.tistory.com/292)



## Model 

사용할 구조체의 타입을 선언한다. (최하위 컴포넌트와 같은 느낌)

```swift
struct FruitModel: Identifiable {
    let id : String = UUID().uuidString 
    let name : String
    let count : Int
}
```

swift 파일을 생성하고, 구조체를 작성한다. <br/>
필수적으로 고유 아이디 값을 생성하고 이를 문자열로 변환하는 코드`UUID().uuidString`를 포함 해야 한다. 


## ViewModel 

모델을 불러와서 로직을 작성한다. (훅이나 핸들러와 같은 느낌)

```swift
class FruitViewModel: ObservableObject {
    
    // property
    
    // 상태 변수도 변화 값에 따라 처리 해야 하니, 뷰모델에서 선언한다.
    //published wrapper는 @state와 같은 기능의 상태값을 선언한다. 클래스에서는 published를 사용
    @Published var fruitArray : [FruitModel] = [] // 모델에서 객체 불러오기 
    @Published var isLoading : Bool = false 

    init() {
        getFruit()
    } // 처음에 불러오면 getFruit 함수를 실행 / 만약 선언하지 않으면 나타나지 않음 

    // function
    
    // fruit 생성하고, 배열에 추가하는 함수
    func getFruit() {
        let fruit1 = FruitModel(name: "딸기", count: 1)
        let fruit2 = FruitModel(name: "사과", count: 2)
        let fruit3 = FruitModel(name: "바나나", count: 7)
        
        // 3초 딜레이 후, 배열에 값 삽입하기
        isLoading = true
        DispatchQueue.main.asyncAfter(deadline: .now() + 3.0) {
            self.fruitArray.append(fruit1)
            self.fruitArray.append(fruit2)
            self.fruitArray.append(fruit3)
            self.isLoading = false
        }
    }
    
    // fruit 삭제 하는 함수
    func deleteFruit(index: IndexSet) {
        fruitArray.remove(atOffsets: index)
    }
}
```

모델과 같이 swift로 파일을 생성하되, 클래스로 작성한다. 


## View

뷰모델을 객체화 해서 사용한다. (단순히 UI만 그림)

### `@StateObject` 와 `@ObservedObject`

- 공통점 : 뷰모델을 객체화 하여 뷰에 불러와 사용할 수 있도록 한다. 
- 차이점 : `@StateObject`는 부모 뷰에서, `@ObservedObject`는 자식 뷰에서 사용한다. 

```swift
struct FruitView: View {
    
    @StateObject var fruitVeiwModel = FruitViewModel()

    NavigationView{
            List {
                if fruitVeiwModel.isLoading {
                    ProgressView()
                } else {
                    ForEach(fruitVeiwModel.fruitArray) { fruit in
                        HStack {
                            
                            Text("\(fruit.count)")
                                .font(.headline)
                                .foregroundColor(.blue)
                            
                            Text(fruit.name)
```

---

## ios 17 

### ViewModel 

ios 17 부터 뷰모델에서 `ObservableObject` 대신 `@Obsevavle`을 사용한다. <br/>

*기존에 뷰모델 작성하는 법*

```swift
// MARK: - 기존에 만들었던 뷰 모델 방식
class OriginalViewModel: ObservableObject {
    let name: String = "vm1"
    @Published var number: Int = 0
    @Published var isClick: Bool = false
}
```

*ios 17 부터*

```swift
// MARK: - ios17부터
@Observable
class NewVersionViewModel {
    let name : String = "vm2"
    var number : Int = 0
    var isClick : Bool = false
}
```

### View

ios 17부터 뷰에서 `@EnvironmentObject` 대신 `@Environment`을 사용한다.  <br/>

*기존에 뷰모델을 뷰로 가져오는 법*

```swift
struct OriginalView: View { 
    @EnvironmentObject private var vm1 : OriginalViewModel
}
```

*ios 17 부터*

```swift
struct NewVersionView: View {
 @Environment(NewVersionViewModel.self) private var vm2
    
    var body: some View {
        // ios 17은 Bindable해줘야 바디와 연결 가능
        @Bindable var vm2 = vm2
    }
}
```

### 전역에서 뷰모델 사용하는 경우 

최상단 뷰에서 전역 변수를 생성한다. <br/>

*기존에 전역 변수 생성하는 법*

```swift
@main
struct MVVMProjectApp: App {
    @StateObject private var vm1 = OriginalViewModel()

    var body: some Scene {
        WindowGroup {
            OriginalView()
                .environmentObject(vm1)
        }
    }
}
```

*ios 17 부터*

```swift
@main
struct MVVMProjectApp: App {
    @State private var vm2 = NewVersionViewModel()

    var body: some Scene {
        WindowGroup {
            NewVersionView()
                .environment(vm2)
        }
    }
}
```