![header](https://capsule-render.vercel.app/api?type=Waving&section=header&height=200&text=NodeRand&fontAlignX=50&fontAlignY=35&color=gradient&fontSize=100&fontColor=ffffff&desc=Frontend%20%C2%B7%20Platform%20Engineer)
-----

<p align="center">
  <samp>
    <a href="https://www.festi.co.kr">페스티컴퍼니</a> ·
    <a href="mailto:nohjunho@festi.co.kr">nohjunho@festi.co.kr</a>
  </samp>
</p>

### 프론트엔드에서 출발해 배포 · 인증 · 인프라까지 맡는 엔지니어

React · TypeScript 기반의 **프론트엔드**를 중심에 두고, 서비스가 사용자에게 닿기까지 필요한
**배포 · 확장성 · 인증 · 보안** 영역을 함께 맡습니다. 주로 하는 일은 셋입니다.

1. 멀티테넌트 CI/CD와 다중 도메인 배포를 직접 운영합니다.
2. 트래픽이 몰리는 상황을 견디도록 인프라를 설계합니다.
3. 인증 경계와 공개 엔드포인트를 점검합니다.

<br>

## 💻 Approach
* 증상과 원인을 분리하고, 문제가 어느 층에 있든 **끝까지 따라 내려가서** 원인을 확인합니다. 고친 뒤에는 **재발하지 않도록** 설계 단계까지 손봅니다.
* **되돌릴 수 있는 결정과 없는 결정**에 다른 무게를 둡니다. 신중할 곳과 가볍게 갈 곳을 먼저 나눕니다.
* **"더 나은 것"이 아니라 "지금 맞는 것"** — 무엇을 내주고 무엇을 얻었는지 말할 수 있어야 설계 결정이라고 생각합니다.
* **조용히 실패하는 것**을 가장 경계합니다. 실패가 소리를 내게 만드는 데 시간을 씁니다.
<br>

## 🏗️ Building
현재 아래와 같은 서비스를 개발·운영하고 있습니다.

|서비스|설명|사이트|
|:---|:---|:---|
|**디지털 가이드**|행사별 공식 안내 사이트|[아산 성웅 이순신축제](https://asan428.festimap.kr) · [경희대학교](https://adelante.festimap.kr) · [2026 택슐랭축제](https://taxchelin.festimap.kr) · [2026 제주레저힐링축제](https://m.jejulhfestival.kr) · [당진 삽교호 드론라이트쇼](https://djdrone.kr)|
|**서비스 모듈**|행사에 붙이는 기능 단위 서비스<br>(공통된 코드와 인프라를 공유하며 개별 서비스 확장)|[스탬프투어](https://jejulhfestival.stamp.festiv.kr) · [행사 지도](https://asan428.map.festiv.kr) · [실시간 주차 혼잡도](https://jejulhfestival.parking.festiv.kr) · [프로그램 예약](https://firefestivaljeju.program.festiv.kr) · [쿠폰북](https://taxchelin.couponbook.festiv.kr) · [현장 투표](https://asan428.vote.festiv.kr) · [셔틀 안내](https://asan428.ride.festiv.kr) · [라이브 송출](https://sium-sium.live.festiv.kr)|
|**PC 사이트**|지역축제 PC 웹사이트|[2026 여수밤바다불꽃축제](https://ysff.co.kr) · [2026 목포 해상 W쇼](https://mokpowshow.co.kr) · [제주레저힐링축제](https://jejulhfestival.kr)|
|**통합로그인**|행사별 SSO|*리뉴얼 중*|
|**백오피스**|16개 행사 서비스의 운영 도구|*리뉴얼 중*|
|**공간관리 시스템**|국내 대학 산학협력 기관 입주기업 관리|기관 내부 시스템, 링크 없음|

> 위 서비스 코드는 전부 **사내 비공개 저장소**에 있습니다. 이 계정에 공개된 저장소는 학습 기록입니다.

<br>

## ⚙️ Engineering
* **엣지 컴퓨팅** — 정적 SPA에서 동적 메타태그 (Lambda@Edge · CloudFront Functions 2단)
* **오토스케일링** — 초 단위 버스트 트래픽 대응 (ASG 프리웜 · 클린 베이스 AMI · SSM 런타임 주입), k6 **1,500 VU** 부하검증 · **p95 6.4s** · **실패율 0%**
* **SSO 인증** — NextAuth 기반 서브도메인 쿠키 설계 · 테스트 환경 분리
* **API 인증 설계** — 무인증 공개 엔드포인트를 **SigV4 + IAM 2겹**으로 차단
* **테스트 도입** — 0 → **251파일 / 4,639 케이스** (2026-08 기준). "얼마나 많이"보다 "어디서 멈출지"를 먼저 정함. **변형 테스트(mutation testing)** 로 테스트 자체를 재검증 (177종 중 174종 검출)
* **인시던트 대응** — 서버 침해 사고 · nginx `start-limit-hit` 로 인한 서버 전면 다운 · OOM 위험 진단
* **프레임워크 전환** — Next.js → React + Vite 회귀. 다만 전부 통일하지 않고, 근거가 있는 곳은 그대로 둠
* **DX 인프라** — 여러 서비스를 한 번에 관리하는 템플릿 레포, 인프라 · 공통 ui 패키지 · 문서 파이프라인 · 버전 관리 스크립트
* **CI/CD** — GitHub Actions · OIDC 인증 · 서브도메인 프로비저닝 자동화

<br>

## 🛠️ Tech Stack
|Kind|Stack|
|:---|:---|
|Language|![typescript](https://img.shields.io/badge/typescript-3178C6?logo=typescript&logoColor=white) ![javascript](https://img.shields.io/badge/javascript-F7DF1E?logo=javascript&logoColor=white)|
|Frontend|![react](https://img.shields.io/badge/react-61DAFB?logo=react&logoColor=white) ![vite](https://img.shields.io/badge/vite-646CFF?logo=vite&logoColor=white) ![nextJS](https://img.shields.io/badge/nextJS-333333?logo=nextdotjs&logoColor=white) ![tailwindCSS](https://img.shields.io/badge/tailwindCSS-06B6D4?logo=tailwindcss&logoColor=white) ![react-router](https://img.shields.io/badge/react--router-CA4245?logo=reactrouter&logoColor=white) ![tanstack query](https://img.shields.io/badge/tanstack%20query-FF4154?logo=reactquery&logoColor=white) ![redux toolkit](https://img.shields.io/badge/redux%20toolkit-764ABC?logo=redux&logoColor=white) ![react-hook-form](https://img.shields.io/badge/react--hook--form-EC5990?logo=reacthookform&logoColor=white) ![tiptap](https://img.shields.io/badge/tiptap-000000)|
|Auth|![nextauth](https://img.shields.io/badge/nextauth-000000?logo=auth0&logoColor=white)|
|Test|![vitest](https://img.shields.io/badge/vitest-6E9F18?logo=vitest&logoColor=white) ![testing library](https://img.shields.io/badge/testing%20library-E33332?logo=testinglibrary&logoColor=white) ![storybook](https://img.shields.io/badge/storybook-FF4785?logo=storybook&logoColor=white) ![k6](https://img.shields.io/badge/k6-7D64FF?logo=k6&logoColor=white)|
|Infra|![github actions](https://img.shields.io/badge/github%20actions-2088FF?logo=githubactions&logoColor=white) ![aws S3](https://img.shields.io/badge/aws%20S3-232F3E) ![aws CloudFront](https://img.shields.io/badge/aws%20CloudFront-232F3E) ![lambda@edge](https://img.shields.io/badge/lambda@edge-232F3E) ![aws EC2 · ASG](https://img.shields.io/badge/aws%20EC2%20%C2%B7%20ASG-232F3E) ![aws SSM](https://img.shields.io/badge/aws%20SSM-232F3E) ![aws Route53](https://img.shields.io/badge/aws%20Route53-232F3E) ![nginx](https://img.shields.io/badge/nginx-009639?logo=nginx&logoColor=white) ![NCP](https://img.shields.io/badge/NCP-03C75A?logo=naver&logoColor=white)|
|Tool|![eslint](https://img.shields.io/badge/eslint-4B32C3?logo=eslint&logoColor=white) ![prettier](https://img.shields.io/badge/prettier-F7B93E?logo=prettier&logoColor=white) ![claude code](https://img.shields.io/badge/claude%20code-D97757?logo=anthropic&logoColor=white)|

<br>

## 📝 History
* **(주)페스티컴퍼니 창립멤버** — 프론트엔드 총괄 (2026 ~ )
* 온라인 축제 팜플렛 서비스 [페스티맵(Festimap)](https://www.festi.co.kr) 프론트엔드 개발 참여 (2023 ~ 2025)
* 세종대학교 소프트웨어학과 졸업 (2020 ~ 2026)
* 멋쟁이사자처럼 at 세종대학교 프론트엔드 트랙 과정 11기 수료 (2023 ~ 2024)
* 2023-2 세종대학교 소프트웨어학과 학술제 수상 (2023)
