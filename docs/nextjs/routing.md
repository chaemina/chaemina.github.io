---
layout: default
title: 라우팅 
parent: Next.js
nav_order: 2
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

페이지가 폴더 단위로 생성되기 때문에, 프로젝트의 규모가 커질 수록 헷갈리기 쉽다. 

### 파일 규칙 

- `layout` 세그먼트 및 해당 하위 항목에 대한 공유 UI
- `page` 경로의 고유한 UI 및 경로에 공개적으로 액세스 
- `loading` 세그먼트 및 해당 하위 항목에 대한 UI 로드 중일 때 
- `not-found` 세그먼트 및 해당 하위 항목에 대한 오류 UI 
- `error` 세그먼트 및 해당 하위 항목에 대한 오류 UI
- `global-error` 전역 오류 UI 
- `route` 서버 측 API 엔드포인트 
- `template` 전문적으로 다시 렌더링 된 레이아웃 UI
- `default` 병렬 경로에 대한 대체 UI


### 구성 요소 계층

Directory Structure

```markdown
folder
| - layout.js
| - error.js
| - loading.js
| - innerFolder
     | - layout.js
     | - error.js
     | - loading.js
     | - page.js
```

Component Hierarchy

```jsx
<Layout>
  <ErrorBoundary fallback={<Error />}>
    <Suspense fallback={<Loading />}>
       <Layout>
         <ErrorBoundary fallback={<Error />}>
            <Suspense fallback={<Loading />}>
              <Page />
            </Suspense>
        </ErrorBoundary>
      </Layout>
    </Suspense>
  </ErrorBoundary>
</Layout>
```


