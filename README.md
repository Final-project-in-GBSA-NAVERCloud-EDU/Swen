# 🔮 Swen

운세를 확인할 수 있는 모바일 중심 웹 서비스.
뉴스, 기사, 글 등을 TTS를 이용하여 음성으로 들려주는 앱 서비스

---

## 📌 프로젝트 요약

- **프로젝트명**: Swen
- **목표**: 바쁜 일상 속, 특히 출퇴근길에 손을 쓰기 어려운 상황에서도
           관심 있는 뉴스나 정보를 TTS(음성 변환)를 통해 편리하게 청취할 수 있도록
           기사를 읽어주는 앱 서비스를 개발하는 것이 목표입니다.
- **기술 스택**:  
  - FrontEnd: `Kotlin(Android)`, `Jetpack Composet`
  - BackEnd : `Kotlin`, `SpringBoot`, `Gradle`, `RestAPI`
  - Infra: `GitHub Actions`, `Docker`, `Naver Cloud Platform`
  - AI 연계 : `Clova Voice`, `Clova Dubbing`, `RAG`, `Agent`
  - API 연동: `네이버 API`, `로컬 JSON`
  - 인증: `Naver OAuth`
- **팀원 구성**:  
  - 이민혁 : OAuth 및 스크랩 구현, 보안 Route 구축
  - 양한진 : 뉴스 수집 및 RAG-Agent 구축
  - 윤종서 : TTS 및 Dubbing 연동, 화면 구축
  - 정유진 : 인프라 및 화면 구축

---

## 🧠 기획 의도

- 최근 사람들은 바쁜 일상 속에서 정보를 접할 시간이 부족해졌고,
  특히 출퇴근 시간에는 스마트폰을 직접 조작하기 어렵습니다.
  이에 따라, 사용자가 관심 있는 뉴스나 정보를 손을 사용하지 않고
  음성으로 편하게 청취할 수 있는 서비스를 기획하게 되었습니다.
  단순히 텍스트를 음성으로 변환하는 것에 그치지 않고,
  사용자의 관심사 기반 기사 추천, 자연스러운 목소리 제공, 청취 환경에
  최적화된 UX 등을 고려하여 설계하고자 했습니다.

---

## 🛠 주요 기능 (Features)

| 기능 | 설명 |
|------|------|
| ✅ 네이버 소셜 로그인 | OAuth2 기반 네이버 계정으로 간편 로그인 |
| ✅ 관심 기사/뉴스 검색  | 사용자의 키워드 기반 기사 검색 + Vector DB 유사도 기반 추천 |
| ✅ RAG 기반 정보 검색 | RAG(Retrieval-Augmented Generation) 방식으로 관련 콘텐츠 추출 |
| ✅ 음성 변환 (Clova Voice) | 기사/뉴스 내용을 TTS 기술로 자연스럽게 음성 변환 |
| ✅ 음성 스타일 선택 (Clova Dubbing) | 사용자가 원하는 목소리 스타일(예: 연예인, 캐릭터 등) 선택 가능 |
| ✅ 스크랩 및 저장 | 스크랩한 콘텐츠를 MySQL DB에 저장하고 나중에 다시 들을 수 있음 |

---

## 🏗️ 아키텍처

DDD(Domain Driven Design) 구조 + Profile 기반 환경 분리

```
src/main/kotlin/
├── Application.kt                # 메인 애플리케이션
├── domain/                       # 도메인 레이어
├── infrastructure/               # 인프라 레이어
├── application/                  # 애플리케이션 레이어
└── presentation/                 # 프레젠테이션 레이어

src/main/resources/
├── application.yaml              # 기본 설정
├── application-local.yaml        # 로컬 환경
└── application-ncp.yaml          # NCP 운영 환경
```

---

## 📷 결과 화면 예시

> (아래 스크린샷은 실제 구현된 결과를 캡쳐하여 삽입)

<table>
    <tr>
       <td align="center" valign="top">
      <b>📲 소셜 로그인</b><br/>
      <img src="./public/Swen_소셜로그인.PNG" width="420"/>
    </td>
        <td align="center" valign="top">
      <b>🏠 메인 페이지</b><br/>
      <img src="./public/Swen_메인페이지.PNG" width="420"/>
    </tr>
  <tr>
    </td>
    <td align="center" valign="top">
      <b>📝 청취 페이지</b><br/>
      <img src="./public/Swen_청취페이지.PNG" width="420"/>
    </td>
    <td align="center" valign="top">
      <b>🔍 스크랩 목록 페이지</b><br/>
      <img src="./public/Swen_스크랩목록.PNG" width="420"/>
    </tr>
</table>

---

## ⚙️ 비기능 요건 (Non-Functional)

| 항목                 | 설명                                                           |
| ------------------ | ------------------------------------------------------------ |
| ✅ 반응형 UI 및 모바일 최적화 | 다양한 디바이스 환경(PC, 태블릿, 모바일)에 대응할 수 있도록 반응형 레이아웃과 터치 최적화 UI 구현  |
| ✅ 성능 최적화           | 컴포넌트의 불필요한 렌더링을 방지하고 렌더링 비용을 최소화하여 사용자 경험(UX) 개선             |
| ✅ 재사용성 및 유지보수성 향상  | 공통 로직은 커스텀 훅으로 추출하고, 조건부 렌더링 및 상태 분리를 통해 코드의 재사용성과 유지보수성 강화  |
| ✅ API 호출 비용 최적화    | 유료 API 호출 횟수를 줄이기 위해 mock 데이터를 활용한 개발 전략을 병행                 |
| ✅ 클린 아키텍처 설계       | 로직과 UI를 명확히 분리하고, 역할 기반으로 폴더 구조 및 컴포넌트 책임을 구분하여 구조적 개발 환경 유지 |

---

## 🚀 추후 확장 계획

| 항목 | 내용 |
|------|------|
| 🗂️ 음성 저장 기능  | Object Storage를 활용하여 변환된 음성을 저장하고, 재청취 기능 제공 |
| ✍️ 스크립트 생성 고도화 | 프롬프트 최적화, 카테고리 기반 분기 처리, 사용자 관심사 기반 스크립트 생성 |
| 📰 뉴스 공유 기능 | 카카오톡 등 SNS 플랫폼으로 뉴스 오디오/텍스트 결과 공유 가능 |
| 📊 오늘의 인기 뉴스 | 사용자가 원하는 뉴스/기사 콘텐츠를 저장해두고 원하는 시간에 청취 가능 |
| 📚 유저 대시보드 | 청취 수 기반으로 오늘 가장 많이 들은 기사/뉴스를 랭킹 형태로 제공 |
| 🎯 개인 맞춤 뉴스 추천 | 사용자 히스토리 및 관심 주제를 기반으로 콘텐츠 큐레이션 강화 |

---

## 🌍 환경별 설정

### Local (로컬 개발)
- 로컬 MySQL 사용
- 디버그 로깅 활성화
- 개발용 API 키

### NCP (운영 환경)
- NCP Cloud DB for MySQL
- NCP Object Storage (음성 파일)
- NCP Cloud Functions 연동
- 운영 최적화 설정

---

### 3. 헬스체크 & 설정 확인
- **헬스체크**: http://localhost:8080/health
- **설정 확인**: http://localhost:8080/test/config
- **API 테스트**: http://localhost:8080/test/naver-news

## 📡 API 엔드포인트

### 시스템
- `GET /health` - 서버 상태 및 환경 정보
- `GET /test/config` - 현재 설정 확인

### 테스트
- `GET /test/naver-news` - 네이버 뉴스 API 테스트
- `GET /test/hyperclova` - 하이퍼클로바 스크립트 생성 테스트

### 뉴스 (예정)
- `POST /api/news/collect` - 뉴스 수집
- `GET /api/news/random` - 랜덤 뉴스 조회

## 🔑 환경변수 가이드

- 노션 참고

## 🚀 NCP 배포 준비사항

1. **NCP Cloud DB for MySQL** 생성
2. **NCP Object Storage** 버킷 생성  
3. **NCP VPC** 및 보안그룹 설정
4. **환경변수** NCP 운영값으로 설정
5. **APP_PROFILE=ncp**로 배포

## 🔧 다음 단계

1. **MySQL 데이터베이스 연결** (유진과 협업)
2. **NCP 환경 구축** 
3. **Repository 구현체 작성**
4. **Vector DB 연동** (RAG 구현)
5. **NCP Object Storage 연동** (음성 파일 저장)

---

## 🧪 프로젝트 사용 방법 (Usage)

### 1. 프로젝트 클론
```bash
git clone https://github.com/NAVER-CLOUD-3-ANDROID/swen-springboot
cd swen-springboot
npm install
```
### 2. 실행
```bash
npm run start
```