---
layout: default
title: 레이아웃
parent: Next.js
nav_order: 3
---


# 레이아웃
{: .no_toc }

여러 페이지에서 공유되는 UI이다. 
{: .fs-6 .fw-300 }

상태를 보존하며 상호 작용이 유지되고, 다시 렌더링 되지 않는다. <br/>
경로의 **레이아웃은 기본적으로 중첩**된다. <br/>
각 상위 레이아웃은 React children prop을 사용하여 그 아래 하위 레이아웃을 래핑한다. <br/>
**서버 구성 요소**이지만, 클라이언트 구성 요소로 설정 할 수 있다. <br/>
데이터를 가져 올 순 있지만, 상위 레이아웃과 하위 레이아웃 간의 데이터 전달은 불가능하다. <br/>

```jsx
export default function Layout({children}) {
      return (
         <section>
             <nav></nav>
             {childre}
         </section> )}
```



## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 루트 레이아웃 (필수)

디렉토리의 최상위 수준에서 정의, **app의 모든 경로에 적용**되는 레이아웃이다. (error, not-found page에도 적용됨) <br/>
Next.js는 루트 레이아웃이 자동 생성되지 않아서 내장된 SEO 지원을 사용하여 HTML 요소로 관리해야 한다. 

```jsx
export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        <h1>첫번째 레이아웃</h1>
        {children}
      </body>
    </html>
  );
}
```

{: .highlight}
💡 루트 레이아웃에만 `<html>`및 `<body>` 태그가 포함 될 수 있다. 

**서버 구성 요소**이며, 클라이언트 구성 요소로 설정 할 수 없다. 

## 중첩 레이아웃 

폴더 내부에 정의 된 레이아웃은 특정 경로 세그먼트에 적용되고, 해당 세그먼트가 활성화 될 때 렌더링 된다. <br/>

```markdown
app
|- layout.jsx
|- page2
  | - page.jsx
  | - layout.jsx
```

기본적으로 파일 계층 구조의 레이아웃은 중첩되어 있다. 


<img src="../../../assets/images/layout1.png" alt="layout" aria-label="layout Image" width="500" height="300">

```jsx
export default function Page2layout({ children }) {
  return (
    <section>
      <h2>두번째 레이아웃</h2>
      {children}
    </section>
  );
}
```
children prop으로 하위 레이아웃을 매핑한다. <br/>
즉, 루트 레이아웃 (app/layout.jsx) 은 page2 레이아웃 (app/page2/layout.jsx) 을 래핑하고, page2 레이아웃은 내부 경로 
세그먼트 (app/page2/*) 를 래핑한다. 


```markdown
app
|- layout.jsx
|- page2
  | - page.jsx
  | - layout.jsx // page2,3에 적용!
  | - page3
```

page2와 page3에 동일한 레이아웃을 적용하고 싶다면, 상위 폴더 (page2) 내부에 layout을 작성한다. 

<img src="../../../assets/images/layout2.png" alt="layout" aria-label="layout Image" width="500" height="300">


{: .highlight}
💡 레이아웃은 자신보다 하위의 요소들을 props로 받기 때문에 해당 페이지의 상위 (해당 폴더도 포함) 레이아웃은 모두 적용된다. 

## 레이아웃 vs 템플릿 

레이아웃은 리렌더링을 하지 않는 반면 템플릿은 리렌더링을 한다. <br/>
레이아웃과 템플릿을 섞어 쓰는 것을 권장하지 않으며, 보통 레이아웃을 사용한다. 