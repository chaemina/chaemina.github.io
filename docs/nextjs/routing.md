---
layout: default
title: 2. 라우팅 
parent: Next.js
---


# Routing
{: .no_toc }

Next.js는 파일 시스템 라우팅을 사용하기에 파일 구조에 따라 경로가 결정된다. 
{: .fs-6 .fw-300 }


<img src="../../../assets/images/router.png" alt="router" aria-label="Router Image" width="600" height="600">

url은 세그먼트(segment)의 집합이다. 

각 폴더는 URL 세그먼트에 매핑 되는 경로 세그먼트이다. 

중첩 된 경로는 폴더를 중첩시켜 표현한다.
아래의 사진 참조 

<img src="../../../assets/images/router2.png" alt="router" aria-label="Router Image" width="600" height="600"> 


기존에는 페이지 라우터를 사용했으나, 최신 기능 사용을 위해 앱 라우터 사용할 것 권장하고 있다. 


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## App Router 

[React Server Components](http://127.0.0.1:4000/docs/nextjs/#csr%EA%B3%BC-ssr)를 기반으로 구축되었다. 
```
app
  |- layout.jsx
  |- page.jsx
```
사용자가 애플리케이션 루트(/)에 방문 할 때 렌더링된다. 

1. 기존의 page.modules.css와 favicon.ico 파일(불필요)제거 

2. layout.jsx 파일 수정 
```jsx
export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  )}
```

3. page.jsx 파일 수정
```jsx
export default function Page() {
  return <h1>Hello, Next.js!</h1> }
```


### Directory structure

<img src="../../../assets/images/router3.png" alt="router" aria-label="Router Image" width="600" height="600"> 

폴더 내부에 page.jsx 파일 작성 <br/>
`/folderName` <br/>
중첩 경로 생성 시, 폴더 내부의 폴더에 page.jsx 파일 작성 <br/>
`/folderName/innerFolder`

{: .warning }
폴더 내부에 page.jsx 파일 생성 하지 않으면 페이지 생성 되지 않음!

