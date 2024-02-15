---
layout: default
title: Next.js
nav_order: 2
has_children: true
permalink: docs/nextjs
---

# Next.js 
{: .no_toc }

Next.js란?
{: .fs-6 .fw-300 }

풀스택 웹 애플리케이션 구축 React 프레임 워크이다. <br/>
React 컴포넌트가 사용자 인터페이스를 구축하면, Next.js는 추가 기능과 최적화를 수행한다. <br/> 
번들링과 컴파일 등 같이 React에 필요한 도구를 추상화하고 자동 구성함으로써 구성에 드는 시간 낭비를 절감시키고 애플리케이션 구축에 집중할 수 있도록 한다. 

CSR과 SSR
{: .fs-6 .fw-300 }

## CSR

client side rendering : 클라이언트 측에서 렌더링 

1. 유저가 웹 사이트에 방문하면 브라우저가 서버에 컨텐츠를 요청한다
1. 서버는 빈 뼈대만 있는 HTML을 응답한다
1. 브라우저가 연결 된 JS링크를 통해 서버로부터 다시 JS 파일을 다운받는다
1. JS를 통해 동적으로 페이지를 만들고 띄운다

### 장점 

- 초기 구동 이후 로딩 속도가 빠르다
- TTV와 TTI 사이 간극이 없다 
- 서버 부하가 분산된다

### 단점 

- 초기 구동 속도가 느리다
- SEO에 불리하다 

## SSR

server side rendering : 서버 측에서 렌더링 

1. 유저가 웹 사이트에 방문하면 브라우저가 서버에 컨텐츠를 요청한다 
1. 서버는 필요한 데이터를 즉시 얻어와 모두 삽입하고 css까지 적용하여 렌더링 준비를 마친 HTML, JS 코드를 브라우저에 응답한다
1. 브라우저는 JS 코드를 다운 받고 HTML에 JS 로직을 연결한다

### 장점 

- 초기 구동이 빠르다
- SEO에 유리하다

### 단점 

- TTV와 TTI 사이 간극이 있다 
- 서버 부하가 있다 


왜 Next.js를 사용할까?
{: .fs-6 .fw-300 }

기존의 리액트를 사용하면서 생기는 단점들(CSR의 단점)을 보완하고자 등장했다. <br/>
Next.js는 초기 구동 속도가 빠르며 검색 엔진에 최적화 되어있다. <br/>
또한 Next.js에서는 SSR 뿐만 아니라 클라이언트 구성요소임을 명시하여 CSR도 사용할 수 있다. 

[참조](https://eun-jee.com/post/front-end/nextjs/01-what_is_nextjs_and_why_use/) 

