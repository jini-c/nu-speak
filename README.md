<p align="center">
  <img src="docs/nuspeakLogo.png" alt="nu:speak logo" width="220">
</p>

<h1 align="center">nu:speak — AI 개인 맞춤 뉴스 에이전트</h1>

<p align="center">
  EQ 슬라이더로 관심도를 조절하고, <b>요약 · TTS · 4컷만화</b>로 뉴스를 가볍게 소비하는 차세대 뉴스 플랫폼
</p>

<p align="center">
  <a href="https://github.com/jini-c/nu-speak/stargazers">
    <img src="https://img.shields.io/github/stars/jini-c/nu-speak?style=flat" alt="GitHub stars">
  </a>
  <a href="https://github.com/jini-c/nu-speak/issues">
    <img src="https://img.shields.io/github/issues/jini-c/nu-speak?style=flat" alt="GitHub issues">
  </a>
  <img src="https://img.shields.io/badge/Node-18%2B-informational?logo=node.js" alt="Node 18+">
  <img src="https://img.shields.io/badge/Next.js-14-informational?logo=nextdotjs" alt="Next.js">
  <img src="https://img.shields.io/badge/Express.js-API-informational?logo=express" alt="Express.js">
  <img src="https://img.shields.io/badge/TypeScript-Yes-informational?logo=typescript" alt="TypeScript">
</p>

<p align="center">
  <a href="#-핵심-기능">핵심 기능</a> ·
  <a href="#-프로젝트-구조">프로젝트 구조</a> ·
  <a href="#-디자인--브랜딩-스토리">디자인 & 브랜딩</a> ·
  <a href="#-스크린샷">스크린샷</a> ·
  <a href="#-환경변수">환경변수</a> ·
  <a href="#-빠른-시작">빠른 시작</a> ·
  <a href="#-api-요약">API 요약</a> ·
  <a href="#-아키텍처">아키텍처</a> ·
  <a href="#-기술-스택">기술 스택</a> ·
  <a href="#-로드맵">로드맵</a> ·
  <a href="#-문서">문서</a> ·
  <a href="#-contributing">Contributing</a> ·
  <a href="#-라이선스">라이선스</a> ·
  <a href="#-크레딧">크레딧</a>
</p>

---

## ✨ 핵심 기능

- **개인화 피드**: EQ 슬라이더(예: IT 60%, 경제 25%, 스포츠 15%)를 실시간 반영해 뉴스 **비중/정렬** 조정
- **AI 콘텐츠 가공**: 1줄/3줄 요약, **TTS(음성)**, **4컷 만화** 변환으로 멀티모달 소비 지원
- **대화형 에이전트**: “오늘 IT 뉴스 알려줘” 같은 자연어 질의로 **피드/요약/관련 기사** 제공
- **저장 & 알림(설계)**: 북마크, 키워드 알림(후속 구현용 API 포함)

---

## 🧭 프로젝트 구조

> 현재 리포 **루트 → `nuspeak/`** 폴더 안에 실제 소스가 있습니다.

```text
nuspeak/
├─ backend/                 # Express API 서버
│  ├─ routes/               # /news, /ai, /auth 등 라우터
│  ├─ services/             # 뉴스 수집, 요약/만화/TTS 연동
│  ├─ app.js                # 서버 엔트리
│  ├─ package.json
│  └─ .env.example          # 서버 환경변수 템플릿 (실제 키는 .env)
│
├─ frontend/                # Next.js 웹 프론트엔드
│  ├─ pages/                # index, news, onboarding, settings
│  ├─ components/           # NewsCard 등
│  ├─ public/               # 정적 자산 (logo.png 등)
│  ├─ styles/
│  ├─ package.json
│  └─ tsconfig.json
│
├─ docs/                    # 문서/이미지
│  ├─ nuspeakLogo.png
│  ├─ API 명세서.docx
│  ├─ Nu_Speak_기획서_V2.docx
│  ├─ 사용자 시나리오.docx
│  ├─ 와이어프레임 구성 가이드.docx
│  ├─ 발표자료_nuspeak_최종.pptx
│  ├─ screen-landing.png    # 랜딩 스크린샷
│  └─ screen-feed.png       # 피드 스크린샷
│
├─ .gitignore
├─ README.md
└─ SETUP.md                 # (선택) 설치/개발 메모
🎨 디자인 & 브랜딩 스토리
브랜드 콘셉트: 신뢰(딥블루) + 혁신(민트). 말풍선(뉴스)과 파형/보이스(음성) 모티프.

직접 제작: 로고부터 프론트 UI까지 팀 콘셉트에 맞춰 직접 제작.
개발 생산성 향상을 위해 Cursor 등 도구를 보조적으로 활용했지만, UX 흐름·브랜딩·컴포넌트 톤앤매너의 최종 의사결정은 팀이 주도했습니다.

디자인 시스템

타이포 위계: Headline/Body/Meta 구분, 가독성 중심

컴포넌트: 카드형 뉴스, EQ 슬라이더, 토스트/알림, 태그/배지, 스켈레톤 로딩

스타일: 4/8 spacing scale, 2xl 라운드, 소프트 섀도, 반응형·접근성 고려

🖼️ 스크린샷
<p align="center"> <img src="docs/screen-landing.jpg" alt="랜딩 — 히어로 섹션(메인 메시지·CTA) + 가치 제안 카드" width="85%"> </p> <p align="center"><em>랜딩: “정보의 바다에서 당신만의 섬을…” 메인 메시지 + ‘지금 시작하기’ CTA</em></p> <p align="center"> <img src="docs/screen-feed.jpg" alt="추천 뉴스 피드 — 카테고리 탭, 카드형 뉴스(태그·요약·메타)" width="85%"> </p> <p align="center"><em>피드: 관심사 탭 전환, 카드형 뉴스 목록(카테고리 태그 · 요약 · 출처 · 메타)</em></p>
⚙️ 환경변수
backend/.env (실제 값은 여기에, 커밋 금지)
bash
복사
편집
# OpenAI / TTS
OPENAI_API_KEY=
GOOGLE_TTS_API_KEY=

# Server
PORT=4000
frontend/.env.local (브라우저에 공개 가능한 값만 사용)
bash
복사
편집
# API 서버 베이스 URL
NEXT_PUBLIC_API_BASE_URL=http://localhost:4000
주의: Next.js의 NEXT_PUBLIC_ 접두사는 브라우저에 공개됩니다. 비밀키는 절대 넣지 마세요.

🚀 빠른 시작
1) 백엔드 (Express)
bash
복사
편집
cd nuspeak/backend
npm install
# 환경변수: .env.example을 복사해 .env 생성 후 값 채우기
npm run dev    # 기본: http://localhost:4000
2) 프론트엔드 (Next.js)
bash
복사
편집
cd nuspeak/frontend
npm install
# .env.local에 NEXT_PUBLIC_API_BASE_URL 설정
npm run dev    # 기본: http://localhost:3000
🔌 API 요약
뉴스 피드 — GET /news/feed?limit=10&page=1

json
복사
편집
{
  "items": [
    {
      "id": "news_123",
      "category": "IT",
      "title": "구글, 새로운 AI 개발 도구 발표",
      "summary_1line": "개발자용 AI 도구 발표",
      "source": "TechCrunch",
      "published_at": "2025-06-26T08:30:00Z",
      "personalization_score": 0.92,
      "recommendation_reason": "IT 관심도 60% 반영"
    }
  ],
  "page": 1,
  "limit": 10
}
EQ 설정 업데이트 — PUT /users/eq-settings

json
복사
편집
{ "eq": { "IT": 60, "경제": 25, "스포츠": 15 }, "is_temporary": false }
AI 대화 — POST /chat/message

json
복사
편집
{ "message": "오늘 IT 뉴스 알려줘" }
요약/만화/TTS

POST /ai/summary — 1줄/3줄 요약

POST /ai/comic — 4컷 만화 스토리+이미지

POST /ai/tts — MP3 TTS 변환

상세 파라미터/응답 구조는 docs/API 명세서.docx 참고.

🧠 아키텍처
mermaid
복사
편집
flowchart LR
  U[사용자] <--> FE[Next.js 프론트엔드]
  FE <--> BE[Express 백엔드 API]
  BE -->|요약/만화/TTS| AI[(OpenAI 등)]
  BE -->|뉴스 수집/캐시| News[(수집기/캐시)]
EQ 반영 시퀀스(개요)

mermaid
복사
편집
sequenceDiagram
  participant User
  participant FE as Frontend
  participant BE as Backend
  User->>FE: EQ 슬라이더 조절(IT 60%)
  FE->>BE: PUT /users/eq-settings { eq, is_temporary }
  BE-->>FE: 200 OK
  FE->>BE: GET /news/feed
  BE-->>FE: 개인화 점수 반영된 목록
  FE-->>User: 재정렬된 피드 표시
🧩 기술 스택
Frontend: Next.js(SSR/SSG), TypeScript, CSS Modules

Backend: Node.js + Express

AI/ML: OpenAI API(요약/대화), TTS API

DB/Caching(설계): PostgreSQL, Redis

CI/CD(옵션): GitHub Actions, Vercel/Render

🗺️ 로드맵
 EQ 디바운스(0.5s) & 실시간 미리보기

 Redis 캐시로 피드 응답 속도 개선

 북마크/키워드 알림 API

 4컷 만화 프롬프트 템플릿 고도화

 모바일 앱 PoC(여유 시)

📚 문서
docs/Nu_Speak_기획서_V2.docx

docs/사용자 시나리오.docx

docs/와이어프레임 구성 가이드.docx

docs/API 명세서.docx

docs/발표자료_nuspeak_최종.pptx

🤝 Contributing
PR 환영합니다. 버그/개선 제안은 Issues에 남겨주세요.

📄 라이선스
MIT (변경 가능)

🙌 크레딧
Team nu:speak — 한국폴리텍대학 정수캠퍼스 AI소프트웨어과

브랜딩 & 프론트 UI: 팀 콘셉트에 맞춰 직접 제작(로고·컬러·타이포·컴포넌트).