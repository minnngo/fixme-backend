# FIXME — AI 기반 영어 교정 웹 서비스 (Backend)

텍스트·음성·사진 어떤 방식으로 입력해도 AI가 영어 문장을 바로 교정해 주는 웹 서비스의 백엔드 저장소입니다.

> IT 동아리 잇츠미(ITSME) 2기 프로젝트 · 2025.03 ~ 2025.08 · 3인 팀

<br>

## 📌 주요 기능

- **텍스트·음성·이미지 교정:** 입력 유형을 판별해 AI 서버로 전달하고, 교정 결과를 반환
- **학습 리포트:** 날짜별 말하기(음성)·쓰기(이미지) 피드백 내역 조회
- **학습 진도:** 주간(1~4주차)·월간 학습 시간과 레벨 변화 데이터 제공
- **회원:** 회원가입, 로그인

<br>

## 🏗 Architecture

```
Client (Svelte)
   │  텍스트 / 음성(Base64) / 이미지(Base64)
   ▼
Spring Boot  ── 요청 유형 판별, 회원·리포트·학습 진도 관리 ── MySQL
   │
   ▼
Flask AI Server  ── OCR(Tesseract), 문법·어휘·표현 교정 모델
```

<br>

## 🛠 Tech Stack

| 구분 | 기술 |
| --- | --- |
| Backend | Java, Spring Boot, Spring Data JPA, Lombok |
| Database | MySQL |
| AI Server | Flask, Tesseract OCR |
| Frontend | Svelte |
| Design | Figma |

<br>

## 🙋‍♀️ My Role

- 기존 영어 교정 서비스 조사를 바탕으로 요구사항 정의, Figma 화면 설계
- 회원·리포트·학습 진도·AI 교정 API 7개 명세 작성 및 구현
- Spring Boot ↔ Flask AI 서버 연동
- MySQL 사용자·피드백·학습 기록 DB 설계

<br>

## 📄 API

| 기능 | Method | URL |
| --- | --- | --- |
| 회원가입 | POST | `/signup` |
| 로그인 | POST | `/login` |
| 말하기 리포트 조회 | GET | `/mypage/report/voice` |
| 쓰기 리포트 조회 | GET | `/mypage/report/image` |
| 주간 학습 진도 조회 | GET | `/mypage/progress/weekly` |
| 월간 학습 진도 조회 | GET | `/mypage/progress/monthly` |
| AI 교정 요청 | POST | `/correction` |

<br>
