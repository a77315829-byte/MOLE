> 이 레포는 팀 프로젝트 [kimhonggyeong/MOLE](https://github.com/kimhonggyeong/MOLE)의 fork입니다.
> 포트폴리오 목적으로 본인 담당 부분을 아래에 정리했습니다.

## 🙋 My Role — 윤정우

**담당: 논문 검색 기능 · 공통 UI/프론트엔드 (Unity 클라이언트)**

### 1. 논문 검색 화면 (`Thesis_Scene`)
- 키워드 입력 → FastAPI 서버(`/paper/papers`) 호출 → PubMed 논문 결과를 카드 UI로 표시하는 흐름 구현
- **최신순 / 관련도순** 정렬 검색 지원
- 서버에서 번역된 한국어 제목·초록을 받아 목록 카드 → 상세 화면(제목, 저자, 저널, 발행일, 초록)으로 전환
- 검색 중 로딩 표시, 빈 입력·서버 요청 실패 시 안내 메시지 처리
- 주요 코드: `PaperFetcher.cs`, `PaperCardUI.cs`, `PaperCardHandler.cs`, `PaperDetailUI.cs`

### 2. 공통 UI · 설정 화면 (`Option_Scene`)
- 탭 전환, 토글, 스크롤 그룹 등 여러 화면에서 쓰는 공통 UI 컴포넌트 제작
- 해상도에 따라 UI 크기를 맞추는 스케일러
- BGM·효과음 설정과 씬 전환 후에도 유지되는 사운드 매니저
- 공지사항, 로그아웃 팝업, 로딩 애니메이션
- 코드 위치: [`MOLE_UNITY/Assets/Jungwoo/`](MOLE_UNITY/Assets/Jungwoo/)

### 성과
- 🥇 2025학년도 신한대학교 창업경진대회 **금상** (팀 EduMoleculAR)
- 📄 2025 (사)융복합지식학회 추계학술발표대회 발표 — 「AI 기반 3차원 시뮬레이션 화학 학습 시스템의 설계 및 구현」

---

# 🧪 MOLE
### AI 기반 3D 화학 학습 시스템

MOLE은 화학 분자 구조를 직접 탐색하고 학습할 수 있도록 개발한  
**Unity 기반 AI 화학 학습 애플리케이션**입니다.

분자 구조의 2D·3D 시각화뿐만 아니라 화합물 검색, 분자 조립,
AI 챗봇, 개인화 퀴즈 추천, 관련 논문 검색 기능을 하나의 학습 환경으로 통합했습니다.

> 신한대학교 교내 마이크로스톤 프로젝트로 개발되었습니다.

---

## 📌 주요 기능

### 🧬 1. 분자 구조 시각화
- 화학 분자의 2D / 3D 구조 시각화
- 분자 회전, 확대 및 축소
- RDKit 및 Open Babel을 활용한 분자 구조 처리
- 분자 구조의 3D 좌표 생성 및 변환

### 🔨 2. 분자 조립
- 사용자가 원자와 결합을 직접 조합하여 분자 생성
- 생성된 분자 구조를 3D 모델로 시각화
- 분자 구조 데이터 처리 및 검증

### 🔍 3. 화합물 검색
- PubChem API 기반 화합물 검색
- 분자식, 구조 및 화합물 정보 조회
- 검색 결과를 기반으로 2D / 3D 분자 구조 제공

### 🤖 4. AI 화학 챗봇
- KoGPT2 기반 화학 학습 질의응답
- 화학·생물학 관련 학습 데이터 기반 응답
- Unity 클라이언트와 AI 서버 연동

### 📝 5. 개인화 퀴즈 추천
- 사용자의 문제 풀이 기록 저장
- 정답 여부 및 학습 데이터를 활용한 추천
- PyTorch 기반 개인화 퀴즈 추천 모델

### 📚 6. 논문 검색
- PubMed API를 통한 화학·생물학 관련 논문 검색
- 논문 제목 및 초록 제공
- 번역 기능을 통한 한국어 학습 지원

---

## 🏗 System Architecture

```text
┌──────────────────────────────┐
│          Unity Client        │
│                              │
│  3D Molecule Visualization   │
│  Molecule Builder / Search   │
│  Quiz / Chatbot / Paper UI   │
└──────────────┬───────────────┘
               │ REST API
               ▼
┌──────────────────────────────┐
│        Python Backend        │
│                              │
│  Molecule Processing         │
│  AI Chatbot                  │
│  Quiz Recommendation         │
│  External API Integration    │
└──────┬────────┬──────────────┘
       │        │
       ▼        ▼
   Database   External API
 MySQL/SQLite PubChem/PubMed
