# nu:speak — AI 개인 맞춤 뉴스 에이전트

nu:speak은 AI‑Agent가 사용자의 취향(EQ 슬라이더, 행동 로그)을 반영해 뉴스를 **추천/요약/음성/만화(4컷)** 등 다양한 형식으로 가공해 주는 차세대 뉴스 소비 플랫폼입니다.

## ✨ 핵심 기능
- **개인화 피드**: EQ 슬라이더(예: IT 60%, 경제 25%, 스포츠 15%) 반영
- **콘텐츠 가공**: 1줄/3줄 요약, TTS 음성, 4컷 만화 생성
- **AI 대화**: “오늘 IT 뉴스 알려줘” 같은 자연어 질의
- **알림/북마크**: 관심 키워드 기반 알림, 저장/공유

## 🧱 기술 스택
- Frontend: React(+Vite/Next) · Tailwind
- Backend: Node.js(Express) 또는 FastAPI
- AI/ML: OpenAI API(LangChain), 추천 로직
- DB/Infra: PostgreSQL · Redis(캐싱)
- 기타: TTS, 이미지 생성 API

## 📡 주요 API
- `GET /news/feed` — 개인화 뉴스 목록
- `PUT /users/eq-settings` — EQ 슬라이더 업데이트
- `POST /chat/message` — AI 대화·요청 처리
- `POST /ai/summary | /ai/comic | /ai/tts` — 요약/만화/TTS

## 🚀 로컬 실행(예시)
```bash
# 1) 의존성 설치
npm i        # 또는 yarn

# 2) 환경변수
cp .env.example .env   # 키값 채우기

# 3) 개발 서버
npm run dev  # 또는 yarn dev
