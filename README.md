# NAVER-CLOUD-3-ANDROID

네이버클라우드 3조 Android 프로젝트입니다.  
본 오거나이제이션은 SWEN 뉴스 재생 앱의 **프론트엔드와 백엔드 서버 개발**을 위한 공동 작업 공간입니다.

---

## 📱 프로젝트 소개

**SWEN (Speak the World Every News)**  
: 매일 아침 대표 뉴스 기사를 스크립트로 변환하고, 이를 **음성으로 읽어주는 앱**을 개발합니다.

- 📰 **뉴스 요약 및 음성 변환** - HyperCLOVA 기반 스크립트 생성 + Clova Voice TTS
- 🤖 **AI 관련 뉴스 추천** - RAG(검색 증강 생성) 기반 개인화 뉴스 추천
- 🔊 **실시간 뉴스 재생** - 원클릭으로 뉴스 듣기 + 관련 뉴스 자동 추천
- 📦 **SpringBoot 기반 백엔드** - 네이버클라우드플랫폼 통합 API 서버
- 🎨 **Android 앱 UI** - Flutter 기반 UI

---

## 📁 레포지토리 구성

| 이름          | 설명                             | 주요 기능 |
|---------------|----------------------------------|-----------|
| [`swen-backend`](https://github.com/NAVER-CLOUD-3-ANDROID/swen-springboot) | SpringBoot 기반 백엔드 서버 | 뉴스 TTS + RAG 추천 API |
| [`swen-app`](https://github.com/NAVER-CLOUD-3-ANDROID/swen-app)         | Android 프론트엔드 앱     | 뉴스 재생 + 추천 UI |

---

## 🧑‍💻 팀원 소개

- 👩‍💻 [양한진](https://github.com/hanzyn09) – **서버 개발 리드** - 뉴스 수집, LLM 활용 스크립트 작성, TTS 연동, RAG 시스템 구축, 로그인 연동
- 👨‍💻 [윤종서](https://github.com/winter-816) – **음성 처리 담당** - TTS 연동, 음성 품질 최적화, 발표
- 👩‍💻 [이민혁](https://github.com/MinhyeokChoco) – **프로젝트 매니저** - JWT token 연동, 일정 관리, 팀 코디네이션
- 👩‍💻 [정유진](https://github.com/juj990717) – **인프라 및 UI** - NCP 인프라 구축, Android 화면 구현

---

## 🔧 기술 스택

### Backend
- **Framework**: Java 17, Spring Boot 3.5.3, Spring Data JPA
- **AI/ML**: HyperCLOVA X (스크립트 생성 + 임베딩), Clova Voice (TTS)
- **Database**: MySQL 8.0, 벡터 검색 시스템
- **Build**: Gradle, REST API, Spring Cloud OpenFeign

### Frontend  
- **Framework**: Flutter

### Infra & DevOps
- **Cloud**: 네이버클라우드플랫폼 (NCP)
- **Storage**: Object Storage (음성 파일 저장)
- **CI/CD**: Docker

### AI 기술
- **RAG (검색 증강 생성)**: 벡터 임베딩 기반 관련 뉴스 추천
- **TTS**: 자연스러운 한국어 음성 변환
- **자동 학습**: 사용자 피드백 기반 추천 시스템 개선

---

## 🚀 주요 기능

### 🎵 **원클릭 뉴스 재생**
- 플레이 버튼 한 번으로 최신 뉴스 즉시 재생
- 주제별 뉴스 검색 및 맞춤 재생
- 고품질 TTS로 자연스러운 음성 제공

### 🤖 **AI 기반 관련 뉴스 추천**
- 현재 재생 중인 뉴스와 관련된 뉴스 3-5개 자동 추천
- 벡터 유사도 기반 정확한 관련성 분석
- 사용할수록 개선되는 개인화 추천

### ⚡ **실시간 자동 학습**
- 매일 자동으로 최신 뉴스 수집 및 벡터화
- 사용자 행동 패턴 학습을 통한 추천 품질 향상
- 콜드 스타트 문제 해결 (첫 사용자도 즉시 추천 가능)

---

## 🗓️ 프로젝트 일정

- **개발 기간**: 7월 10일 ~ 7월 28일 (3주)
- **협업 방식**: 매주 월/수/금 회의 및 코드 리뷰
- **최종 발표**: 7월 29일 (화)
- **주요 마일스톤**:
 - 1주차: 기본 TTS 기능 구현
 - 2주차: RAG 추천 시스템 개발
 - 3주차: 앱 통합 및 최적화

---

## 🌐 서비스 아키텍처
```
[Android App]
↓ REST API
[Spring Boot Server]
↓
┌─────────────────────┐
│ 1. 네이버 뉴스 API    │ → 뉴스 검색
│ 2. HyperCLOVA X     │ → 스크립트 생성 + 임베딩
│ 3. Clova Voice      │ → TTS 변환
│ 4. RAG 추천 시스템   │ → 관련 뉴스 검색
└─────────────────────┘
↓
[NCP Object Storage] → 음성 파일 저장
[MySQL Vector DB]    → 뉴스 임베딩 저장
```
---

## 📊 성과 및 차별점

### 🏆 **기술적 성과**
- **완전한 RAG 구현**: 검색-증강-생성 파이프라인 구축
- **자동화 시스템**: 스케줄링 기반 무인 운영 가능
- **콜드 스타트 해결**: 초기 사용자도 즉시 서비스 이용 가능
- **확장 가능한 아키텍처**: 마이크로서비스 기반 설계

### 🎯 **차별화 요소**
- **네이버클라우드플랫폼 생태계 완전 활용**
- **사용할수록 똑똑해지는 AI 추천**
- **원클릭 사용성**: 복잡한 설정 없이 즉시 이용
- **실시간 학습**: 최신 뉴스 트렌드 자동 반영

---

## 📄 기타

- 📌 **협업 방식**: GitHub Issue 및 Pull Request 기반 협업
- 📝 **문서화**: 코드 컨벤션, 커밋 메시지 규칙 등은 팀 노션 참고
- 🔧 **API 문서**: Swagger UI 제공 (http://localhost:8080/swagger-ui.html)
- 🧪 **테스트**: 단위 테스트, 통합 테스트, API 테스트 포함
- 📈 **모니터링**: 실시간 성능 추적 및 에러 모니터링

---

> **SWEN**은 단순한 뉴스 앱을 넘어, **AI 기반 개인화 뉴스 추천 플랫폼**으로 발전했습니다. 🚀
