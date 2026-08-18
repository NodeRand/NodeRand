![header](https://capsule-render.vercel.app/api?type=Waving&section=header&height=200&text=NodeRand&fontAlignX=50&fontAlignY=35&color=gradient&fontSize=100&fontColor=ffffff&desc=Here's%20NodeRand%20GitHub)
-----

<p align="center">
  <samp>
    <a href="https://www.festi.co.kr">페스티컴퍼니</a> ·
    <a href="mailto:nohjunho@festi.co.kr">nohjunho@festi.co.kr</a>
  </samp>
</p>

### 프론트엔드로 시작해, 그 아래 인프라까지 내려온 개발자 🤗
학부 팀에서 축제 사이트 하나로 시작해, 그게 회사가 됐고, 지금은 그 위의 서비스들을 굴리고 있음.
화면부터 시작했지만 문제가 프론트 바깥에 있는 경우가 많아 **인증 · 배포 · 확장성 · 보안**까지 따라 내려옴.
<br>

## 🧠 Approach 🧠
* 문서를 먼저 읽기보다 **부딪혀 해결한 뒤 이름을 붙이는** 순서
* 이슈가 끝나면 개념 단위로 쪼개 기록 — 개인 볼트에 **개념 300여 개 · 계열 8개**를 링크로 연결
* 깊이는 의도적으로 조절 — 백엔드는 **읽고 리뷰할 수준**까지, 그 이상은 멈춤
* "더 나은 안"보다 **무엇을 내주고 무엇을 얻었는지** 말할 수 있는 결정

<br>

## 🎪 Building 🎪
아래와 같은 서비스를 개발·운영하고 있음.

|서비스|한 줄|
|:---|:---|
|**디지털 가이드**|행사별 공식 안내 사이트|
|**서비스 모듈**|스탬프투어 · 지도 · 주차 혼잡도 · 프로그램 예약 · 쿠폰북 · 라이브 송출|
|**통합로그인**|행사별 SSO · *리뉴얼 중*|
|**백오피스**|16개 행사 서비스의 운영 도구 · *리뉴얼 중*|
|**PC 사이트**|지역축제 PC 웹사이트|
|**공간관리 시스템**|국내 대학 산학협력 기관 입주기업 관리 · 기관 내부 시스템이라 링크 없음|

[아산 성웅 이순신축제](https://asan428.festimap.kr) ·
[경희대학교](https://adelante.festimap.kr) ·
[2026 택슐랭축제](https://taxchelin.festimap.kr) ·
[2026 제주레저힐링축제](https://m.jejulhfestival.kr) ·
[당진 삽교호 드론라이트쇼](https://djdrone.kr) ·
[2025 여수밤바다불꽃축제](https://ysff.co.kr) ·
[2026 목포 해상 W쇼](https://mokpowshow.co.kr) ·
[제주레저힐링축제](https://jejulhfestival.kr)

[스탬프투어](https://jejulhfestival.stamp.festiv.kr) ·
[행사 지도](https://asan428.map.festiv.kr) ·
[실시간 주차 혼잡도](https://jejulhfestival.parking.festiv.kr) ·
[프로그램 예약](https://firefestivaljeju.program.festiv.kr) ·
[쿠폰북](https://taxchelin.couponbook.festiv.kr) ·
[라이브 송출](https://sium-sium.live.festiv.kr)

> 위 서비스 코드는 전부 **사내 비공개 저장소**. 이 계정의 공개 저장소는 아래 두 섹션.

<br>

## ⚙️ Engineering ⚙️
구현해 본 것들.

* **엣지 컴퓨팅** — 정적 SPA에서 동적 메타태그 (Lambda@Edge · CloudFront Functions 2단)
* **오토스케일링** — 초 단위 버스트 트래픽 대응 (ASG 프리웜 · 클린 베이스 AMI · SSM 런타임 주입), k6 **1,500 VU** 부하검증 · **p95 6.4s** · **실패율 0%**
* **SSO 인증** — NextAuth 기반 서브도메인 쿠키 설계 · 테스트 환경 분리
* **API 인증 설계** — 무인증 공개 엔드포인트를 **SigV4 + IAM 2겹**으로 차단
* **테스트 도입** — 0 → **251파일 / 4,639 케이스**, "얼마나 많이"가 아니라 "어디서 멈출지" 기준. **변형 테스트(mutation testing)** 로 테스트 자체를 재검증 (177종 중 174종 검출)
* **인시던트 대응** — 서버 침해 사고 · nginx `start-limit-hit` 로 인한 서버 전면 다운 · OOM 위험 진단
* **프레임워크 전환** — Next.js → React + Vite 회귀. 다만 전부 통일하지 않고, 근거가 있는 곳은 그대로 둠
* **DX 인프라** — 템플릿 레포 · 공통 ui 패키지 · 문서 파이프라인 · 버전 관리 스크립트
* **CI/CD** — GitHub Actions · OIDC 인증 · 서브도메인 프로비저닝 자동화

<br>

## 📚 Studying 📚
* [자바 · 스프링부트](https://github.com/NodeRand/all-in-one-backend-study) — 백엔드를 읽고 리뷰할 수 있는 수준까지
* [Next.js SSO](https://github.com/NodeRand/next-sso-study) — 통합로그인 구축 전 사전 학습
* [AX 활용](https://github.com/NodeRand/catch-up-ax-class) — 백오피스 자동화 에이전트 방향
* [Cursor AI](https://github.com/NodeRand/we-can-cursor-study) · [React Native](https://github.com/NodeRand/react-native-expo-cli-study) · [Next.js](https://github.com/NodeRand/next-js-study-one-bite) · [React](https://github.com/NodeRand/nomad-react-master)

<br>

## 🌱 Roots 🌱
* [목포 해상 W쇼](https://github.com/Halo-Festimap/festimap-frontend-mokpo) — 학부 팀으로 맡은 축제 사이트. 지금 회사 일의 시작점
* [피크닉플릭](https://github.com/PicnicFlick/Frontend-server) — 스마트 돗자리 대여 서비스
* [북바오](https://github.com/FourBao-A/Frontend) — 세종대 중고 도서 거래 서비스
* [세종대여](https://github.com/NodeRand/sejong-rent) — 소프트웨어융합대학 학생회 대여 서비스

<br>

## 🛠️ Tech Stack 🛠️
|Kind|Stack|
|:---|:---|
|Language|![Static Badge](https://img.shields.io/badge/C-A8B9CC?style=flat&logo=c&logoColor=white) ![Static Badge](https://img.shields.io/badge/C%2B%2B-00599C?logo=c%2B%2B&logoColor=white) ![Static Badge](https://img.shields.io/badge/python-3776AB?logo=python&logoColor=white) ![Static Badge](https://img.shields.io/badge/java-orange?logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPD94bWwgdmVyc2lvbj0iMS4wIiA%2FPjxzdmcgcm9sZT0iaW1nIiB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI%2BPHRpdGxlLz48cGF0aCBkPSJNOC44NTEgMTguNTZzLS45MTcuNTM0LjY1My43MTRjMS45MDIuMjE4IDIuODc0LjE4NyA0Ljk2OS0uMjExIDAgMCAuNTUyLjM0NiAxLjMyMS42NDYtNC42OTkgMi4wMTMtMTAuNjMzLS4xMTgtNi45NDMtMS4xNDlNOC4yNzYgMTUuOTMzcy0xLjAyOC43NjEuNTQyLjkyNGMyLjAzMi4yMDkgMy42MzYuMjI3IDYuNDEzLS4zMDggMCAwIC4zODQuMzg5Ljk4Ny42MDItNS42NzkgMS42NjEtMTIuMDA3LjEzLTcuOTQyLTEuMjE4TTEzLjExNiAxMS40NzVjMS4xNTggMS4zMzMtLjMwNCAyLjUzMy0uMzA0IDIuNTMzczIuOTM5LTEuNTE4IDEuNTg5LTMuNDE4Yy0xLjI2MS0xLjc3Mi0yLjIyOC0yLjY1MiAzLjAwNy01LjY4OCAwLS4wMDEtOC4yMTYgMi4wNTEtNC4yOTIgNi41NzNNMTkuMzMgMjAuNTA0cy42NzkuNTU5LS43NDcuOTkxYy0yLjcxMi44MjItMTEuMjg4IDEuMDY5LTEzLjY2OS4wMzMtLjg1Ni0uMzczLjc1LS44OSAxLjI1NC0uOTk4LjUyNy0uMTE0LjgyOC0uMDkzLjgyOC0uMDkzLS45NTMtLjY3MS02LjE1NiAxLjMxNy0yLjY0MyAxLjg4NyA5LjU4IDEuNTUzIDE3LjQ2Mi0uNyAxNC45NzctMS44Mk05LjI5MiAxMy4yMXMtNC4zNjIgMS4wMzYtMS41NDQgMS40MTJjMS4xODkuMTU5IDMuNTYxLjEyMyA1Ljc3LS4wNjIgMS44MDYtLjE1MiAzLjYxOC0uNDc3IDMuNjE4LS40NzdzLS42MzcuMjcyLTEuMDk4LjU4N2MtNC40MjkgMS4xNjUtMTIuOTg2LjYyMy0xMC41MjItLjU2OCAyLjA4Mi0xLjAwNiAzLjc3Ni0uODkyIDMuNzc2LS44OTJNMTcuMTE2IDE3LjU4NGM0LjUwMy0yLjM0IDIuNDIxLTQuNTg5Ljk2OC00LjI4NS0uMzU1LjA3NC0uNTE1LjEzOC0uNTE1LjEzOHMuMTMyLS4yMDcuMzg1LS4yOTdjMi44NzUtMS4wMTEgNS4wODYgMi45ODEtLjkyOCA0LjU2MiAwLS4wMDEuMDctLjA2Mi4wOS0uMTE4TTE0LjQwMSAwczIuNDk0IDIuNDk0LTIuMzY1IDYuMzNjLTMuODk2IDMuMDc3LS44ODggNC44MzItLjAwMSA2LjgzNi0yLjI3NC0yLjA1My0zLjk0My0zLjg1OC0yLjgyNC01LjUzOSAxLjY0NC0yLjQ2OSA2LjE5Ny0zLjY2NSA1LjE5LTcuNjI3TTkuNzM0IDIzLjkyNGM0LjMyMi4yNzcgMTAuOTU5LS4xNTMgMTEuMTE2LTIuMTk4IDAgMC0uMzAyLjc3NS0zLjU3MiAxLjM5MS0zLjY4OC42OTQtOC4yMzkuNjEzLTEwLjkzNy4xNjggMC0uMDAxLjU1My40NTcgMy4zOTMuNjM5Ii8%2BPC9zdmc%2B&logoColor=white) ![Static Badge](https://img.shields.io/badge/html-E34F26?logo=html5&logoColor=white) ![Static Badge](https://img.shields.io/badge/css-1572B6?logo=css&logoColor=white) ![Static Badge](https://img.shields.io/badge/javascript-F7DF1E?logo=javascript&logoColor=white) ![Static Badge](https://img.shields.io/badge/typescript-3178C6?logo=typescript&logoColor=white)|
|Framework|![Static Badge](https://img.shields.io/badge/react-61DAFB?logo=react&logoColor=white) ![Static Badge](https://img.shields.io/badge/nextJS-333333?logo=nextdotjs&logoColor=white) ![Static Badge](https://img.shields.io/badge/react%20native-61DAFB?logo=react&logoColor=white)|
|Library| ![Static Badge](https://img.shields.io/badge/react--router-CA4245?logo=react-router&logoColor=white) ![Static Badge](https://img.shields.io/badge/react--hook--form-EC5990?logo=react-hook-form&logoColor=white) ![Static Badge](https://img.shields.io/badge/react--query-FF4154?logo=react-query&logoColor=white) ![Static Badge](https://img.shields.io/badge/recoil-red?logo=recoil&logoColor=white) ![Static Badge](https://img.shields.io/badge/redux-764ABC?logo=redux&logoColor=white) ![Static Badge](https://img.shields.io/badge/framer%20motion-0055FF?logo=framer&logoColor=white)|
|CSS| ![Static Badge](https://img.shields.io/badge/CSS%20Modules-000000?logo=cssmodules&logoColor=white) ![Static Badge](https://img.shields.io/badge/styled--components-DB7093?logo=styled-components&logoColor=white) ![Static Badge](https://img.shields.io/badge/tailwindCSS-blue?logo=tailwindcss&logoColor=white) ![Static Badge](https://img.shields.io/badge/Nativewind-blue?logo=tailwindcss&logoColor=white)|
|Tool| ![Static Badge](https://img.shields.io/badge/create--react--app-09D3AC?logo=create-react-app&logoColor=white) ![Static Badge](https://img.shields.io/badge/eslint-4B32C3?logo=eslint&logoColor=white) ![Static Badge](https://img.shields.io/badge/prettier-F7B93E?logo=prettier&logoColor=white) ![Static Badge](https://img.shields.io/badge/vite-%23646CFF?logo=vite&logoColor=white) ![Static Badge](https://img.shields.io/badge/expo-1C2024?logo=expo&logoColor=white)|
|Deploy| ![Static Badge](https://img.shields.io/badge/github_actions-2088FF?logo=githubactions&logoColor=white) ![Static Badge](https://img.shields.io/badge/github_pages-222222?logo=githubpages&logoColor=white) ![Static Badge](https://img.shields.io/badge/aws-232F3E?logo=amazonwebservices&logoColor=white) ![Static Badge](https://img.shields.io/badge/aws_S3-569A31?logo=amazons3&logoColor=white) ![Static Badge](https://img.shields.io/badge/aws_EC2-FF9900?logo=amazonec2&logoColor=white) ![Static Badge](https://img.shields.io/badge/aws_Route53-8C4FFF?logo=amazonroute53&logoColor=white) ![Static Badge](https://img.shields.io/badge/aws_CloudFront-8C4FFF?logo=icloud&logoColor=white) ![Static Badge](https://img.shields.io/badge/aws%20ACM-CA4245?logo=amazon&logoColor=white) ![Static Badge](https://img.shields.io/badge/nginx-569A31?logo=nginx&logoColor=white) ![Static Badge](https://img.shields.io/badge/certbot-14D8CC?logo=certbot&logoColor=white) ![Static Badge](https://img.shields.io/badge/NCP%20VPC-7738C8?logo=naver&logoColor=white) ![Static Badge](https://img.shields.io/badge/NCP%20Object%20Storage-569A31?logo=naver&logoColor=white) ![Static Badge](https://img.shields.io/badge/NCP%20Server-7738C8?logo=naver&logoColor=white) ![Static Badge](https://img.shields.io/badge/NCP%20Global%20DNS-C5242C?logo=naver&logoColor=white) ![Static Badge](https://img.shields.io/badge/NCP%20Maps-339AF0?logo=naver&logoColor=white)|

<br>

## 📝 History 📝
* **(주)페스티컴퍼니 창립멤버** — 프론트엔드 총괄 (2026 ~ )
* 온라인 축제 팜플렛 서비스 [페스티맵(Festimap)](https://www.festi.co.kr) 프론트엔드 개발 참여 (2023 ~ 2025)
* 세종대학교 소프트웨어학과 졸업 (2020 ~ 2026)
* 멋쟁이사자처럼 at 세종대학교 프론트엔드 트랙 과정 11기 수료 (2023 ~ 2024)
* 2023-2 세종대학교 소프트웨어학과 학술제 수상 (2023)

<br>

## 📈 Activity Graph 📈
[![NodeRand's github activity graph](https://github-readme-activity-graph.vercel.app/graph?username=NodeRand&theme=react)](https://github.com/Ashutosh00710/github-readme-activity-graph)
