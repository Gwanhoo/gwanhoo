# 김관호 | Backend Developer

실시간 데이터 처리와 AI 기능 통합을 중심으로 **서버와 클라이언트 간 데이터 흐름을 설계하는 백엔드 개발자**입니다.

Node.js 기반 API와 Socket.io 실시간 협업 기능을 구현했으며, Python 기반 원격 STT 시스템에서는 오디오 수집부터 GPU 추론, 자막 상태 관리와 화면 표시까지 이어지는 흐름을 다루고 있습니다.

## 관심 분야 및 기술 스택

- **서버 아키텍처**: API, 데이터 모델, 인증과 서비스 간 책임 분리
- **실시간 데이터 처리**: 이벤트 동기화, 작업 큐, 지연과 상태 수명 관리
- **AI 기능 통합**: 모델 호출을 실제 서비스의 입력·응답·오류 처리 흐름에 연결

아래는 프로젝트에서 사용한 기술과 적용 범위입니다. 학습 기록은 하단에 별도로 정리했습니다.

| 영역 | 기술 | 적용 프로젝트 및 경험 |
| --- | --- | --- |
| Backend | Node.js, Express, Python | 칸반·코사모 API 서버, VOXLUX 클라이언트·GPU 서버 |
| Realtime & Communication | WebSocket, Socket.io, HTTP / REST API | 칸반의 프로젝트별 동기화, 코사모 채팅, VOXLUX HTTP 원격 추론 |
| Database | MongoDB, Mongoose | 칸반 데이터 모델·CRUD에 MongoDB/Mongoose, 코사모에 MongoDB driver 사용 |
| AI & ML Integration | OpenAI API, Faster-Whisper, Silero VAD, RunPod GPU | 칸반 작업 분해, VOXLUX 음성 감지·한국어 STT·원격 GPU 실행 |
| Frontend | React, Next.js, Tailwind CSS, PySide6 | 웹 프로젝트 UI, VOXLUX 데스크톱 GUI·자막 오버레이 |
| Development & Infrastructure | Git / GitHub, Vercel, CUDA | 코드 관리, 웹 배포, VOXLUX GPU 추론 환경 사용 |

## Featured Projects

### 1. VOXLUX — AI 기반 실시간 자막 시스템

Windows 시스템 오디오를 원격 GPU 서버에서 한국어로 인식하고, 연속 자막과 투명 데스크톱 오버레이로 표시하는 애플리케이션입니다.

[GitHub](https://github.com/Gwanhoo/Speech-Caption-AI) · [아키텍처](https://github.com/Gwanhoo/Speech-Caption-AI/blob/main/docs/architecture.md) · [문제 해결](https://github.com/Gwanhoo/Speech-Caption-AI/blob/main/docs/troubleshooting.md)

**기술**: Python, PySide6, WASAPI Loopback, HTTP, RunPod GPU, Faster-Whisper, Silero VAD, CUDA

- **오디오 수집과 전송**: WASAPI Loopback으로 시스템 오디오를 수집하고 16 kHz mono로 변환한 뒤, 3초 윈도우·2초 stride로 HTTP 전송
- **원격 추론**: RunPod GPU 서버에서 Silero VAD와 Faster-Whisper를 실행하는 **SINGLE STT** 구조
- **큐와 지연 관리**: bounded queue, 오래된 작업·결과 폐기, timeout과 서버 오류·복구 상태 처리
- **자막 조립과 표시**: 중첩 윈도우의 텍스트 정합, PARTIAL/FINAL 상태 수명 관리, Qt worker와 signal을 통한 GUI·오버레이 갱신

오디오 수집 속도와 원격 추론 속도가 다를 때의 적체, 중복 인식 결과, 화면 상태 관리를 함께 다뤘습니다.

[오디오 파이프라인](https://github.com/Gwanhoo/Speech-Caption-AI/blob/main/docs/audio-pipeline.md) · [자막 처리](https://github.com/Gwanhoo/Speech-Caption-AI/blob/main/docs/subtitle-processing.md) · [성능과 검증 범위](https://github.com/Gwanhoo/Speech-Caption-AI/blob/main/docs/performance.md)

### 2. AI 기반 실시간 협업 칸반 시스템

프로젝트와 태스크를 관리하고, 변경 내용을 실시간으로 공유하며 AI로 작업을 분해하는 협업 시스템입니다.

[GitHub](https://github.com/Gwanhoo/Capstone-Design) · [배포](https://capstone-design-rho.vercel.app/)

**기술**: Next.js, React, Node.js, Express, MongoDB, Mongoose, Socket.io, OpenAI API

- 프로젝트·태스크·멤버 CRUD와 MongoDB/Mongoose 데이터 모델 구성
- Socket.io Room을 이용한 프로젝트 단위 실시간 상태 동기화
- OpenAI API 기반 **Task Decomposition**으로 프로젝트 설명을 작업 목록으로 변환
- REST API로 데이터를 처리하고 WebSocket 이벤트로 변경을 전달하는 혼합 통신 구조

프로젝트별 이벤트 경계를 나누고, 데이터 저장과 실시간 알림을 연결하는 경험을 쌓았습니다.

### 3. 코사모 — 개발자 커뮤니티

게시글·댓글과 실시간 채팅을 제공하는 개발자 커뮤니티 서비스입니다.

[GitHub](https://github.com/Gwanhoo/My_BackEnd_CRUD_Project)

**기술**: Node.js, Express, MongoDB, Socket.io, Passport, Kakao OAuth

- 게시글 CRUD와 댓글 작성·조회
- Socket.io 기반 실시간 채팅
- Passport 기반 로그인·세션 인증과 Kakao OAuth 로그인
- MongoDB를 이용한 게시글·댓글·사용자 데이터 관리

HTTP 요청의 인증 처리와 실시간 채팅 연결을 함께 다뤘습니다.

## Other Projects

### 아비도스 제작 최적화 계산기

[GitHub](https://github.com/Gwanhoo/abydos_app) · [배포](https://abydos-app.vercel.app/)

React, Next.js, Tailwind CSS로 구현한 자원 최적화 계산기입니다. 자원 변환 규칙과 탐색 알고리즘으로 최대 제작량·교환 전략을 계산하고, Lost Ark API의 실시간 시세를 반영해 재료 판매와 제작 후 판매의 손익을 비교합니다. Vercel에 배포했습니다.

### LinkShop

[GitHub](https://github.com/Sprint-11-4team/sprint-linkshop) · [배포](https://project-linkshop.netlify.app)

React 기반 쇼핑몰 팀 프로젝트에서 **상품 수정 및 삭제 UI**를 담당했습니다.

### Linkbrary

[GitHub](https://github.com/codeit-fe11-part3-team4/linkbrary) · [배포](https://fe11-team4-linkbrary.netlify.app/)

React, Next.js, Tailwind CSS 기반 링크 공유 팀 프로젝트에서 **로그인 및 회원가입 UI**를 담당했습니다.

### Coworkers

[GitHub](https://github.com/fe11-part4-team3/coworkers)

React, Next.js, Tailwind CSS 기반 협업 서비스 팀 프로젝트에서 **메인 랜딩 페이지 UI**를 담당했습니다.

## Learning & Documentation

[Backend Learning Log](https://github.com/Gwanhoo/backend-learning-log)

프로젝트 구현 경험과 별도로 Node.js, Express, MongoDB, WebSocket, OpenAI API의 학습 내용과 예제를 정리합니다.

- [Node.js / Express](https://github.com/Gwanhoo/backend-learning-log/blob/main/backend/README.md): REST API와 서버 구조
- [MongoDB](https://github.com/Gwanhoo/backend-learning-log/blob/main/database/README.md): 데이터 모델과 CRUD
- [WebSocket / Socket.io](https://github.com/Gwanhoo/backend-learning-log/blob/main/websocket/README.md): 실시간 통신과 이벤트 동기화
- [OpenAI API](https://github.com/Gwanhoo/backend-learning-log/blob/main/AI/README.md): AI 기능 연동과 작업 분해

## Contact

- GitHub: [Gwanhoo](https://github.com/Gwanhoo)
- Email: [kimgwanho0206@gmail.com](mailto:kimgwanho0206@gmail.com)
