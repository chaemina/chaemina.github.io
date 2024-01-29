---
layout: default
title: 9-4. 프로퍼티
parent: Swift
---


# 프로퍼티
{: .fs-6 .fw-300 }


{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## property

- 저장 프로퍼티 
- 연상 프로퍼티 
- 인스턴스 프로퍼티 
- 타입 프로퍼티 

프로퍼티는 구조체, 클래스, 열거형 내부에서만 구현 할 수 있다.

{: .note-title }
> **주의**
>
> 열거형에서는 연산 프로퍼티만 가능하다. <br/> 연산 프로퍼티는 `var` 키워드로만 선언이 가능하다.

### 구조체 Student의 프로퍼티 작성 

```swift
struct Student {
```

```swift
    // 인스턴스 저장 프로퍼티
    var name : String = ""
    var koreanAge : Int = 0

    // 인스턴스 연산 프로퍼티
    var westernAge : Int {
        // 꺼낼때는 연산 수행해서 리턴
        get {
            return koreanAge - 1
        }
        // 세팅은 매개변수 받아서 연산
        set(inputValue){
            koreanAge = inputValue + 1
        }
    }

    // 타입 저장 프로퍼티
    static var typeProperty : String = "학생"
```

**메소드를 프토퍼티로 변환하기**

```swift
   func selfIntro () {
      print("저는 \(self.name) 입니다.")
   }
 ```

 매개변수 없는 인스턴스 메소드의 경우
 
 ```swift   
    var selIntro : String {
        get {
            return "저는 \(self.name) 입니다."
        }
    }
```

읽기 전용 인스턴스 연산 프로퍼티로 작성한다.

```swift
    
    static func selfIntro() {
        print("학생 타입 입니다.")
    }
```

매개변수 없는 타입 메소드의 경우

```swift    
    static var selfIntro : String {
        return "학생 타입 입니다."
    }   
```

읽기 전용 타입 연산 프로퍼티로 작성한다. (get 생략 가능)


### 프로퍼티 접근 

- 타입 프로퍼티 
```swift
print(Student.selfIntro)
print(Student.typeProperty)
```

- 인스턴스 프로퍼티
```swift
// 인스턴스 생성
var mina : Student = Student()
// 인스턴스 저장 프로퍼티 사용
mina.koreanAge = 23
mina.name = "민아"
print(mina.name)
// 인스턴스 연산 프로퍼티 사용
print(mina.selIntro)
print("한국나이 \(mina.koreanAge) 미국 나이 \(mina.westernAge)")
```

### 프로퍼티 감시자 

프로퍼티 값이 변경 될 때 원하는 동작을 수행한다.
저장 프로퍼티 뒤에 블록 willSet(변경 전) didSet(변경 후)을 작성한다.

{:.warning}
연산 프로퍼티와는 함께 사용할 수 없다.

```swift
struct Age { 
    // 저장 인스턴스와 사용
    var currentAge : Int = 21 {
        willSet(newAge) {
            print("올해는 \(currentAge) 내년에는 \(newAge)")
        }
        didSet(oldAge) {
            print("작년에는 \(oldAge) 올해는 \(currentAge)")
        }
    }
    // willSet, didSet 뒤의 매개 변수 생략 할 수 있음
}
    
var myAge : Age = Age()

myAge.currentAge = 22
// 올해는 21 내년에는 22
// 작년에는 21 올해는 22
```

{:.highlight}
지역 / 전역 변수에서도 사용이 가능하다.

```swift
var a : Int = 100 {
    willSet {
        print("\(a)애서 \(newValue) 로 변경 될 예정입니다.")
    }
    didSet {
        print("\(oldValue) 에서 \(a)로 변경되었습니다.")
    }
}

a = 200
// 100애서 200 로 변경 될 예정입니다.
// 100 에서 200로 변경되었습니다.
```

