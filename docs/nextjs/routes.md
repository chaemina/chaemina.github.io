---
layout: default
title: Routes 
parent: Next.js
nav_order: 6
---


# Routes
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Route Groups

폴더를 경로에 포함 시키고 싶지 않을 때 폴더 이름을 괄호로 묶어 설정한다. 

 `(folderName)`

여러 루트 레이아웃 생성 시 최상위 layout.jsx 파일을 제거하고, 각 경로 그룹내에 파일을 추가한다. 

```markdown 
(root)
| - page.jsx
(another-root)
| - layout.jsx
| - page2
    | - page.jsx
```

위의 사진에 따르면 (root)와 (another-root) 둘다 자체 루트 레이아웃을 가진다. 

{: .warning}
단, "/" 경로를 갖는 파일은 하나여야 한다. 


## Dynamic Routes 

동적 세그먼트의 폴더 이름을 대괄호로 묶어 설정한다. 

 `[folderName] -> [id] or [slug]`

```markdown
page
| - [slug]
    | - page.jsx
```


```jsx
export default function Page({ params }) {
  return <div>My Post: {params.slug}</div>;
}
```

page/1, page/abc 등의 경로로 접근 시 해당 url의 파라미터 값에 접근하여 이를 출력 할 수 있다. 


## Catch-all 

 `[...folderName] -> [...id] or [...slug]`

```markdown
page
| - [...slug]
    | - page.jsx
```


page/1, page/1/1 등의 page의 모든 하위 파라미터에 적용된다. 

## Optional Catch-all 

 `[[...folderName]] -> [[...id]] or [[...slug]]`

 대괄호 두번 감싸면 자신 경로까지 출력할 수 있다. 

## usePathname

현재 url path를 문자열로 반환한다. 


```jsx
“use client”
import {usePathname} from "next/navigation"

export default function Page() {
    const pathname = usePathname();
       ... 
```

<img src="../../../assets/images/usePathname.png" alt="부분 렌더링" aria-label="부분 렌더링 Image" width="500" height="300">


## useSearchParams

쿼리 스트링 url의 쿼리문 부분을 출력한다. 

```jsx
“use client”
import {useSearchParams} from "next/navigation"

export default function Page({params}) {
   const searchParams = useSearchParams();
   const searchTerm = searchParams.get("params");
```

<img src="../../../assets/images/useSearchParams.png" alt="부분 렌더링" aria-label="부분 렌더링 Image" width="500" height="300">


## useSelectedLayoutsegments

해당 슬롯 내의 활성 경로 세그먼트를 읽을 수 있다. 

```markdown
page
| - page.jsx
| - segment1
|   | - page.jsx
| - segment2
|   | - page.jsx
```


```jsx
"use client";

import { useSelectedLayoutSegments } from "next/navigation";

export default function ExampleClientComponent() {
  const segments = useSelectedLayoutSegments();

  return (
    <ul>
      {segments.map((segment, index) => (
        <li key={index}>{segment}</li>
      ))}
    </ul>
  );
}
```

- 루트 페이지에서는 아무것도 출력하지 않는다. 
- 세그먼트 1 페이지에서는 **segment1** 을 출력한다. 
- 세그먼트 2 페이지에서는 **segment2** 을 출력한다. 

즉, 방문 한 하위 세그먼트 값을 출력한다. 


