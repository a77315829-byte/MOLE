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
