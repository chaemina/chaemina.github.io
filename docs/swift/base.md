---
layout: default
title: 2. Swift 시작하기
parent: Swift
---


# Swift 시작하기
인프런의 [해당강의](https://www.inflearn.com/course/%EC%8A%A4%EC%9C%84%ED%94%84%ED%8A%B8-%EA%B8%B0%EB%B3%B8-%EB%AC%B8%EB%B2%95)를 수강하며 작성한 swift 문법 정리 내용이다. 
{: .fs-6 .fw-300 }


{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 명명 규칙 

- lower camel case  ➡️  함수, 메소드 , 변수, 상수 
{: .fs-5 .fw-300  }

- upper camel case ➡️ 타입 (타입, 구조체, 클래스, 이넘)
{: .fs-5 .fw-300  }

💡 upper camel case 는 파스칼 케이스와 같다. 
{: .highlight}


## console

```swift
print() // 단순 문자열 출력 
dump()  // 인스턴스의 자세한 설명 까지 출력 
```

## 문자열 보간법 

```swift
\(변수)
print("\(변수)")
```



## 상수와 변수 

### 선언하기 

키워드(let, var) 이름 : 타입 = 값
{: .fs-5 .fw-300  }


```swift
let letString : String = "상수로 선언 된 문자열"
var varString : String = "변수로 선언 된 문자열"
```

### 상수와 변수 
상수(let)로 선언 된 값은 변경 할 수 없고, 변수(var) 로 선언 된 값은 변경 할 수 있다. 

``` swift
//letString = "상수는 값을 변경 할 수 없다."
varString = "변수는 값을 변경 할 수 있다."
```

### 데이터 타입
값의 데이터 타입이 명확할 땐, 타입을 생략 할 수 있다. 

``` swift
var myBool = true
let myNum = 10
```

단 , 나중에 할당하려는 상수나, 변수를 선언할 때는 타입을 꼭 명시 해야 한다.
``` swift
let num : Int
```



swift에서는 상수와 변수의 차이가 명확하다. <br/> 변하지 않을 값은 상수로, 나중에 수정이 필요한 값은 변수로 선언하도록 주의하자.
{: .warning }

