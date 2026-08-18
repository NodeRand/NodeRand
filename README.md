<p align="center">
  <img src="https://raw.githubusercontent.com/NodeRand/NodeRand/main/header.svg" width="900" alt="노준호 Junho Noh — Co-founder, 페스티컴퍼니" />
</p>

<p align="center">
  <samp>
    <a href="https://www.festi.co.kr">페스티컴퍼니</a> ·
    <a href="mailto:nohjunho@festi.co.kr">nohjunho@festi.co.kr</a>
  </samp>
</p>

축제·행사를 디지털로 옮기는 일을 합니다. 프론트엔드로 시작했지만 지금은 그 아래
**인증 · 배포 · 확장성 · 보안**까지 직접 소유하고 있습니다.

<br>

## 🎪 만들고 운영 중인 것 🎪

### 디지털 가이드

[아산 성웅 이순신축제](https://asan428.festimap.kr) ·
[경희대학교](https://adelante.festimap.kr) ·
[2026 택슐랭축제](https://taxchelin.festimap.kr) ·
[2026 제주레저힐링축제](https://m.jejulhfestival.kr) ·
[당진 삽교호 드론라이트쇼](https://djdrone.kr)

행사 하나당 사이트 하나. 회사 서브도메인(`*.festimap.kr`)뿐 아니라 **고객사 고유 도메인**까지 받습니다.
정적 SPA인데 서브도메인마다 메타태그가 달라야 했고, `동적 메타태그 = SSR` 이라는 통념 때문에
Next.js를 쓰고 있었습니다. **Lambda@Edge(원본 응답) + CloudFront Functions(뷰어 요청) 2단 구조**로
풀어내면서 Next.js를 걷어냈습니다.

### 서비스 모듈

[스탬프투어](https://jejulhfestival.stamp.festiv.kr) ·
[행사 지도](https://asan428.map.festiv.kr) ·
[실시간 주차 혼잡도](https://jejulhfestival.parking.festiv.kr) ·
[프로그램 예약](https://firefestivaljeju.program.festiv.kr) ·
[쿠폰북](https://taxchelin.couponbook.festiv.kr) ·
[라이브 송출](https://sium-sium.live.festiv.kr)

행사에 필요한 기능을 모듈로 쪼개 `<행사>.<서비스>.festiv.kr` 로 붙입니다.
**템플릿 레포 + 공통 ui 패키지**로 신규 행사 셋업을 표준화했고, 위의 엣지 메타태그 구조를 그대로 공유합니다.

### 통합로그인

행사별 SSO. NextAuth 기반 **서브도메인 쿠키 설계**와 테스트 환경 분리까지 직접 구축했습니다.

오픈일 트래픽은 5분간 지속되는 부하가 아니라 **10~20초 안에 몰리는 버스트**라,
메트릭 기반 오토스케일링으로는 구조적으로 못 잡습니다(수집 5분 + 알람 ~15분 + 부팅 수 분).
그래서 **ASG 프리웜 + 클린 베이스 AMI + SSM 런타임 주입** 구조로 설계했습니다.

> k6 **1,500 VU** 버스트 · c6g.medium **4~6대** · **p95 6.4s** · **실패율 0%**
> — 설계·부하검증 완료, 실오픈일 실측은 아직입니다.

*현재 리뉴얼 중 — 공개 예정*

### 백오피스 (비즈니스)

16개 행사 서비스를 운영하는 도구입니다. 테스트가 한 줄도 없던 상태에서
**251파일 / 4,639 케이스**까지 올렸고, "얼마나 많이"가 아니라 **"어디서 멈출지"** 를 매번 근거를 대고 정했습니다.
작성한 테스트가 진짜 잡는지 확인하려고 **변형 테스트(mutation testing)** 로 소스를 일부러 망가뜨려
177종 중 174종 검출을 확인했고, 빠져나간 3종은 동치 변형임을 증명해 근거를 남겼습니다.

*현재 리뉴얼 중 — 공개 예정*

### PC 사이트

[2025 여수밤바다불꽃축제](https://ysff.co.kr) ·
[2026 목포 해상 W쇼](https://mokpowshow.co.kr) ·
[제주레저힐링축제](https://jejulhfestival.kr)

### 그 외

국내 대학 산학협력 기관의 **입주기업 공간관리 시스템** 구축 (2025~).
기관 내부 시스템이라 링크는 두지 않습니다.

<br>

> 위 서비스들의 코드는 전부 **사내 비공개 저장소**에 있습니다.
> 이 계정에 공개된 저장소는 **학습 기록**이고, 실제로 만든 것은 위 링크에서 동작합니다.

<br>

## 🧭 이런 것들을 겪었습니다 🧭

- 무인증 공개 상태였던 **CloudFront 무효화 엔드포인트를 SigV4 + IAM 2겹**으로 닫았습니다. 프론트에 시크릿을 심는 방식은 번들에 그대로 노출되므로 성립하지 않는다는 판단에서 시작했습니다
- 서버 침해 사고, nginx `start-limit-hit` 로 인한 테스트 서버 전체 다운, 스탬프투어 OOM 위험 — **터진 것을 수습하고 재발 구조를 막는 일**을 맡아 왔습니다
- Next.js → React + Vite 회귀. 다만 **통합로그인만은 NextAuth 때문에 Next.js를 유지**합니다. 전부 통일하는 것이 항상 옳지는 않았습니다
- `festimap-frontend-docs` 문서 파이프라인 · 템플릿 패키지 · 버전 관리 스크립트 — **다른 개발자의 속도를 올리는 일**에 시간을 가장 많이 씁니다

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
* **(주)페스티컴퍼니 Co-founder** — 프론트엔드 총괄 (2026 ~ )
* 온라인 축제 팜플렛 서비스 [페스티맵(Festimap)](https://www.festi.co.kr) 프론트엔드 개발 참여 (2023 ~ 2025)
* 세종대학교 소프트웨어학과 졸업 (2020 ~ 2026)
* 멋쟁이사자처럼 at 세종대학교 프론트엔드 트랙 과정 11기 수료 (2023 ~ 2024)
* 2023-2 세종대학교 소프트웨어학과 학술제 수상 (2023)

<br>

## 📈 Activity Graph 📈
[![NodeRand's github activity graph](https://github-readme-activity-graph.vercel.app/graph?username=NodeRand&theme=react)](https://github.com/Ashutosh00710/github-readme-activity-graph)
