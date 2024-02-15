---
layout: default
title: 에러
parent: Next.js
nav_order: 8
---


# 에러
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Error

loading과 동일하게 하위의 요소들에 대한 에러처리가 적용된다. 

```markdown
app
| - page.jsx
| - loading.jsx
| - error.jsx
| - page2
    | - page.jsx
```

```jsx
'use client'
 
import { useEffect } from 'react'
 
export default function Error({ error, reset }) {
  useEffect(() => {
    console.error(error)
  }, [error])
 
  return (
    <div>
      <h2>Something went wrong!</h2>
      <button onClick={ () => reset()}>
        Try again
      </button>
    </div>
  )
}
```

/page 와 /page/page2 에서 동일하게 error 로직이 동작한다. 

{: .warning}
Error components must be Client Components!

### 전역 에러 처리 

app/layout이나 app/template 같은 경우 error.jsx 파일로 에러 처리가 안된다. 

이때 global-error.jsx를 앱의 최상단에 위치시키면 전역적으로 에러를 처리한다. 

```jsx
'use client'
 
export default function GlobalError({ error, reset }) {
  return (
    <html>
      <body>
        <h2>Something went wrong!</h2>
        <button onClick={() => reset()}>Try again</button>
      </body>
    </html>
  )
}
```

### 서버 오류 처리 

서버 컴포넌트에서 오류가 발생하면 Next.js는 에러 객체를 가장 가까운 error파일에 error 속성으로 전딜한다. 



## not-found

404 에러 발생 시 나타날 페이지를 정의한다. 

```jsx
import Link from "next/link";

export default function NotFound() {
  return (
    <div>
      <h2>Not Found</h2>
      <p>Could not find requested resource</p>
      <Link href="/">Return Home</Link>
    </div>
  );
}
```

<img src="../../../assets/images/nextjserror.png" alt="error" aria-label="error Image" width="400" height="200">


{: .note-title }
> **주의**
>
> routes group으로 처리(ex: (root)) 했더라도 not-found.jsx 파일은 app의 최상단에 위치해야한다. 

