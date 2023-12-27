---
layout: default
title: 1. Next.js 시작하기
parent: Next.js
---


# Next.js 시작하기
{: .no_toc }

vscode에서 Next.js를 사용하기 위한 환경을 설정한다. 
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 자동 설치

```yaml
# creat-next-app : 모든 것을 자동으로 설정
npx create-next-app@latest
```

```yaml
What is your project named? my-app 프로젝트 이름
Would you like to use TypeScript? No / Yes 타임 스크립트 사용 여부 
Would you like to use ESLint? No / Yes ESLint 사용 여부 
Would you like to use Tailwind CSS? No / Yes Tailwind css 사용 여부 
Would you like to use src/ directory? No / Yes src 디렉토리 사용 여부 
Would you like to use App Router? (recommended) No / Yes App Router 사용 여부 
Would you like to customize the default import alias (@/)? No / Yes Import 구문 커스텀 여부 
What import alias would you like configured? @/
```

💡 기본적으로 Next.js 는 TypeScript, ESLint 및 Tailwind css 구성과 함께 제공됨 <br/>
`src` 선택적으로 프로젝트 루트에 있는 디렉터리를 사용하여 구성 파일에서 애플리케이션 코드 분석 
{: .highlight}

```yaml
cd my-app
npm run dev # 개발 모드에서 Next.js 시작
```

## 수동 설치

```yaml
npm install next@latest react@latest react-dom@latest
```

package.json

```json
{ 
  "scripts" : {
    "dev" : "next dev", "_comment" : " 개발 모드에서 Next js 시작",
    "build" : "next build", "_comment" : " 프로덕션 용도로 애플리케이션 빌드 ",
    "start" : "next start", "_comment" : " Next.js 프로덕션 서버 시작 ",
    "lint" : "next lint", "_comment" : "내장 ESLint 구성 설정 ", 
   }
}
```
_comment는 주석입니다. 

## npx와 npm의 차이 

자동 설치와 수동 설치를 비교하면서 npx와 npm의 차이에 대해 궁금해져 정리해보았다. 
<br/>

**package.json** 모듈 설치 시 자동으로 생성되는 node.js 버전 관리 파일 <br/>
**node_modules** 모든 모듈의 저장 공간 <br/>
**React** 많은 모듈들로 구성된 라이브러리 <br/>
**npm** 모듈 설치 **node.js** 개발 작업 환경 구성
{: .highlight}
<br/>

Node Package Manager(관리)
{: .fs-6 .fw-300 }

npm은 node.js의 자동화된 의존성과 패키지 관리를 위한 패키지 매니저이다. `npm install`은 원하는 패키지를 로컬(node_modules)에 설치하는 명령어이다. 

npm의 단점 

1. 업데이트 여부 확인 불가(최초 설치로 계속 사용)  
2. 글로벌 모듈(-g) 사용 시 하나의 버전만 사용할 수 있음 
3. 보일러 플레이트에 치명적 (변경사항이 잦아 최신버전 항상 필요)

→ npx는 이를 해결한다. 


Node Package Runner(실행)
{: .fs-6 .fw-300 }

npx는 npm 5.2.0 버전부터 추가된 node.js 패키지를 실행시키는 도구이다. 패키지의 최신 버전 파일을 불러와 실행시키고 실행 이후 해당 패키지를 제거한다. 