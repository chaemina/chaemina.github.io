---
layout: default
title: Linking and Navigating
parent: Next.js
nav_order: 5
---


# Linking and Navigating
{: .no_toc }

경로 탐색의 두 가지 방법 
{: .fs-6 .fw-300 }

- Link component 

- useRouter Hook 

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 경로 탐색 작동 방식 

### Prefetching

사용자가 경로 방문하기 전에 백그라운드에서 경로를 미리 로드한다. 

- `Link`  경로가 사용자의 뷰포트에 표시되면 자동으로 미리 가져온다. Prefetching은 페이지가 처음 로드 될 때 또는 스크롤을 통해 표시 될 때 발생한다. 

- `router.prefetch()`  useRouter 훅을 사용해서 프로그래밍 방식으로 경로를 미리 가져온다. 

{: .warning}
개발 중에는 활성화되지 않고 프로덕션 레벨에서만 동작한다. 

### Caching

Next.js에는 Router Cache 라는 메모리 내 클라이언트 측 캐시가 있다. 사용자가 앱을 탐색 할 때 미리 가져온 경로 세그먼트와 방문한 경로의 React Server 구성요소 페이로드가 캐시에 저장된다. 

**장점** 서버 탐색 시 서버에 새로운 요청을 하는 대신, 캐시를 최대한 재사용하여 요청 수와 전송 되는 데이터 수를 줄여 성능을 향상 시킨다. 


### 부분 렌더링 

변경되는 세그먼트만 리렌더링하고 공유 세그먼트의 상태는 유지한다. 

<img src="../../../assets/images/partrendering.png" alt="부분 렌더링" aria-label="부분 렌더링 Image" width="300" height="100">



## Link 

 `<Link href="path"> 링크명 </Link>` 

```jsx
import Link from "next/link";

export default function Page2() {
  return (
    <>
      <button>
        <Link href="/page3">Page3</Link>
      </button>
      <h1>Hello, Page2!</h1>
    </>
  );
}
```

### href (필수)

탐색 할 경로 또는 URL 

href로 객체의 값도 받을 수 있다. 

*쿼리스트링*

`/about?name=test`

```jsx
<Link href={ pathname: '/about', query: { name: 'test' }}> About us </Link>
```


*URL 파라미터*

`/blog/my-post`

```jsx
<Link href={ pathname: '/blog/[slug]',query: { slug: 'my-post' }}> Blog Post </Link>
```

물론 객체로 받지 않아도 동적 경로 표현은 가능하다. 

```jsx
<Link href={`/blog/${post.slug}`}>{post.title}</Link>
```


### replace

기본 값은 `false`이며, `true`로 설정 시 이동 후 history stack이 삭제된다. 


### passHref legacyBehavior

`<a>` 태그로 구성된 컴포넌트를 하위 요소로 전달 받는 경우 

*하위요소*

```jsx
const Btn = ({ onClick, href }, ref) => {
  return (
    <button>
      <a href={href} onClick={onClick} ref={ref}>
        page 4
      </a>
    </button>
  );
};

export default Btn;
```

*상위에서 Link 사용*

```jsx
<Link href="/page2/page4" passHref legacyBehavior> 
         <Btn />
</Link>
```

## useRouter 

프로그래밍 방식으로 경로를 변경한다. 

```jsx
'use client'
 
import { useRouter } from 'next/navigation'
 
export default function Page() {
  const router = useRouter()
 
  return (
    <button type="button" onClick={() => router.push("/page2/page4")}>
          page4
    </button>
  )
}
```

{: .warning}
클라이언트 구성 요소 내에서만 사용할 수 있다.

