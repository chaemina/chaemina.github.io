---
layout: default
title: 메타 데이터 
parent: Next.js
nav_order: 4
---


# 메타 데이터 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## meta data

각 페이지별 탭의 타이틀을 지정한다. 

<img src="../../../assets/images/metadata.png" alt="meta data" aria-label="meta data Image" width="300" height="100">

```jsx
export const metadata = {
  title: "PAGE2",
};

export default function Page2() {
  return <h1>Hello, Page2!</h1>;
}
```
Page2의 탭 타이틀을 **PAGE2**로 설정한다. 

{: .highlight}
💡 모든 페이지의 탭 타이틀을 통일하고 싶으면 루트 레이아웃에서 지정해준다.

