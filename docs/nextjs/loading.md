---
layout: default
title: 로딩 
parent: Next.js
nav_order: 7
---


# 로딩 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## loading 

React Suspense는 loading.jsx 파일을 사용하여 즉시 로딩 상태 표시 할 수 있다. 

```markdown
app
| - layout.jsx
| - page.jsx
| - loading.jsx
```

### 즉시 로딩 상태 

탐색 시 즉시 표시되는 대체 UI (스켈레톤 및 스피너 등) 를 사전에 렌더링 하여 사용자가 앱이 응답하고 있음을 
이해할 수 있도록 한다. 이는 더 나은 사용자 경헌을 제공하는 데 도움이 된다. 


## 서스펜스를 이용한 스트리밍 

SSR (서버 사이드 렌더링)의 경우, 사용자가 페이지를 보고 상호작용 하기 전에 완료해야 하는 과정이 있다. 

1. 특정 페이지의 모든 데이터를 서버에서 가져온다. 
1. 서버는 페이지의 HTML을 렌더링 한다. 
1. 페이지의 HTML,CSS,JS가 클라이언트로 전송된다. 
1. 비대화형 사용자 인터페이스는 생성된 HTML,CSS를 사용하여 표시된다. 
1. React hrdrates (대화형 인터페이스 생성)

<img src="../../../assets/images/loading.png" alt="lodaing" aria-label="loading Image" width="300" height="100">

모든 데이터를 가져 온 후에만 서버가 페이지의 HTML을 렌더링 할 수 있다. 클라이언트에서 리액트는 페이지의 모든 구성 요소에 대한 코드가 다운로드 된 후에 UI를 하이드레이션 할 수 있다. 

{: .highlight}
🤓 비대화형 페이지를 가능 한 빨리 표시하여 로딩 성능을 향상 시키지만, 여전히 느릴 수 있다. 

그래서 스트리밍을 사용하여 페이지의 HTML을 더 작은 부분으로 나누고, 점진적으로 해당 부분을 서버에서 클라이언트로 전송한다. 

Suspense는 [TTV와 TTI](https://velog.io/@yu2jeong/TTV-Time-To-View-TTI-Time-To-Interact) 간의 간극이 일어나는 사이에 나타나서 사용자가 의미없는 페이지를 보지 않도록 한다. 

```jsx
import { Suspense } from "react";

export const metadata = {
  title: "Another Root",
};

export default function Page5() {
  return (
    <Suspense fallback={<p>loading ...</p>}>
      <h1>Hello, page5!</h1>
    </Suspense>
  );
}
```

