## 👋 안녕하세요! 데이터와 지표로 시스템 병목을 해결하는 백엔드 엔지니어 이재석입니다.

> **"예측 가능한 시스템과 유연한 아키텍처를 지향하며, 정량적 메트릭을 기반으로 문제를 해결합니다."**

- 📊 **성능 최적화**: Prometheus/Grafana 메트릭과 k6 부하 테스트를 통해 DB 커넥션 고갈 병목을 진단하고, WAS 메모리 롤업 연산 전환으로 `P95 응답 지연을 52s에서 42ms로 99.9% 단축(TPS 7/s → 153/s)`했습니다.
- ⚡ **실시간 파이프라인**: 외부 Open API의 세션 유량 제한 극복 및 대용량 실시간 패킷 유입 환경에서 **비동기 이벤트 파이프라인, Redis Lua Script(Write-Back), 인메모리 쓰로틀링**으로 서버 가용성을 보장합니다.
- 🏛️ **견고한 도메인 설계**: 도메인 주도 설계(DDD)의 **식별자 참조 원칙**과 **헥사고날(Port & Adapter) 아키텍처**를 적용하여 비즈니스 로직을 인프라 기술로부터 격리하고 트랜잭션 락(Lock) 경합을 차단합니다.
- 🧪 **테스트 자동화 및 품질 강제**: **Testcontainers** 기반 격리 통합 테스트(215건)와 **JaCoCo 테스트 커버리지 80% 이상 빌드 강제**를 통해 코드의 배포 무결성을 검증합니다.

---

### 🛠️ Tech Stack

**Backend & Languages**
- ![Java 21](https://img.shields.io/badge/Java_21-ED8B00?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot 3.5](https://img.shields.io/badge/Spring_Boot_3.5-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![Spring WebFlux](https://img.shields.io/badge/Spring_WebFlux-6DB33F?style=flat-square&logo=spring&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white) ![JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=flat-square) ![QueryDSL](https://img.shields.io/badge/QueryDSL-0769AD?style=flat-square) ![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)

**Database & Caching**
- ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis_(Lua_/_PubSub)-DC382D?style=flat-square&logo=redis&logoColor=white)

**Realtime & Streaming**
- ![WebRTC](https://img.shields.io/badge/WebRTC_(P2P_Mesh)-333333?style=flat-square&logo=webrtc&logoColor=white) ![WebSocket](https://img.shields.io/badge/WebSocket_(STOMP)-010101?style=flat-square)

**Infra & DevOps**
- ![AWS](https://img.shields.io/badge/AWS_(EC2,_RDS)-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white) ![Docker](https://img.shields.io/badge/Docker_&_Compose-2496ED?style=flat-square&logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)

**Testing & Monitoring**
- ![JUnit5](https://img.shields.io/badge/JUnit5-25A162?style=flat-square&logo=junit5&logoColor=white) ![Testcontainers](https://img.shields.io/badge/Testcontainers-2496ED?style=flat-square) ![JaCoCo](https://img.shields.io/badge/JaCoCo-D22128?style=flat-square) ![Spring REST Docs](https://img.shields.io/badge/Spring_REST_Docs-6DB33F?style=flat-square) ![k6](https://img.shields.io/badge/k6-7D64FF?style=flat-square&logo=k6&logoColor=white) ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white) ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

**Frontend (Sub)**
- ![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![React Native](https://img.shields.io/badge/React_Native-61DAFB?style=flat-square&logo=react&logoColor=black)

---

### 💼 Key Projects

#### 📈 1. AssetMind — 실시간 주가 스트리밍 및 조건별 차트 조회 플랫폼
> **2026.01 ~ 2026.06 | 4인 팀 프로젝트 (백엔드 아키텍처 및 API·파이프라인 전담, 기여도 100%)**[cite: 2]  
> 한국투자증권(KIS) Open API를 연동하여 60개 주요 종목의 실시간 체결·호가 데이터를 유실 없이 수집·브로드캐스팅하고, 고성능 분봉 차트 조회를 제공하는 웹 플랫폼[cite: 2]

- **Tech Stack**: `Java 21`, `Spring Boot 3.5`, `Spring WebFlux`, `WebSocket(STOMP)`, `Redis(Lua)`, `PostgreSQL`, `JPA`, `k6`, `Prometheus`, `Grafana`, `Testcontainers`, `Spring REST Docs`[cite: 2]
- **주요 아키텍처 설계 및 트러블슈팅 성과**:
  - **[차트 조회 DB 병목 해결]** k6 부하 테스트 시 DB 집계 연산으로 발생한 HikariCP 커넥션 풀 고갈 병목을 진단하고, 1분봉 단순 조회 후 WAS 메모리에서 롤업(Roll-up) 연산하도록 전환하여 **P95 응답 지연 52s → 42ms 단축(99.9% 개선), TPS 7/s → 153/s 향상(약 22배), 에러율 5% → 0% 달성**[cite: 2, 11]
  - **[멀티 세션 분산 어댑터]** KIS 웹소켓 API의 계정당 세션 제한(40개) 제약을 극복하기 위해 3개 계정을 연동하여 총 120개 세션을 동적으로 할당·관리하는 커스텀 어댑터 구현[cite: 2]
  - **[비동기 파이프라인 & 동시성 제어]** `ApplicationEventPublisher` 기반 이벤트 파이프라인으로 소켓 수신·적재·브로드캐스팅 스레드를 분리하고, `candle_update.lua` 기반 **Redis Lua Script & Write-Back** 구조와 인메모리 호가 쓰로틀링 적용[cite: 2]
  - **[동적 DB 파티셔닝 & 헥사고날 아키텍처]** 누적되는 시계열 체결(`RawTick`) 데이터의 인덱스 비대화 방지를 위해 JDBC 기반 일자별 테이블 파티션 자동 생성 스케줄러를 구현하고, Port & Adapter 패턴 및 Spring REST Docs API 문서 자동화 구축[cite: 2]

---

#### 🎥 2. [StudyLink](https://github.com/iamwotjr99/group-study) — WebRTC 기반 실시간 온라인 통합 학습 플랫폼
> **2025.09 ~ 2025.12 | 1인 개인 프로젝트 (기여도 100%, 🎓 교내 캡스톤 디자인 우수 졸업논문상 수상작)** 
> 파편화된 스터디 그룹의 모집·생명주기 관리부터 실시간 그룹 채팅 및 WebRTC 기반 P2P 화상 회의를 단일 웹 환경으로 내재화한 통합 학습 플랫폼

- **Tech Stack**: `Java 21`, `Spring Boot 3.5.3`, `Spring Security(JWT)`, `Spring Data JPA`, `QueryDSL`, `MySQL`, `WebSocket(STOMP)`, `WebRTC`, `Docker Compose`, `Nginx`, `AWS(EC2, RDS)`, `Testcontainers`, `JaCoCo`
- **주요 아키텍처 설계 및 트러블슈팅 성과**:
  - **[WebRTC 시그널링 충돌 해결 및 비용 검증]** 3인 이상 다중 접속 시 동시 Offer 패킷 전송으로 발생하는 경쟁 상태(`InvalidStateError` / Glare)를 **Polite Peer 상태 머신 알고리즘**으로 해결하여 **P2P 화상 연결 성공률 100% 달성**
  - **[인프라 부하 최소화 정량 검증]** 소규모 스터디 도메인에 맞춘 P2P Mesh 채택으로 미디어 서버(SFU) 비용을 0원으로 절감하고, AWS CloudWatch 실측 결과 **서버 네트워크 출력 507KB, CPU 사용률 9.11% 미만** 유지 입증
  - **[DDD 도메인 격리 & CQRS 적용]** 순수 자바 도메인 모델과 JPA 영속성 엔티티를 분리하고 애그리거트 간 **ID 식별자 참조 원칙**을 적용해 고빈도 채팅 트랜잭션으로 인한 스터디 도메인 락(Lock) 경합을 차단했으며, 상태 변경(Command)과 화면 조회(**QueryDSL DTO 직접 프로젝션**) 경로를 분리
  - **[STOMP 보안 & 유령 세션 동기화]** `StompJwtChannelInterceptor`로 연결·구독 시점의 2단계 인가 체계를 구축하고, `StompLifecycleEventListener`를 통해 브라우저 강제 종료 시 발생하는 유령 세션(Ghost Session)을 실시간 정리하여 접속자 정합성 100% 유지
  - **[테스트 피라미드 및 품질 통제]** 인메모리 `FakeRepository` 단위 테스트와 `Testcontainers` 격리 통합 테스트 등 **총 215개의 테스트 스위트**를 구축하고, **JaCoCo 커버리지 80% 이상**을 빌드 조건으로 강제

---

### 🎓 Education, Research & Certifications

- **동국대학교 WISE캠퍼스 컴퓨터공학과 졸업** (2020.03 ~ 2026.02)
  - **학점 4.06 / 4.5 (우등 졸업)** | 교내 캡스톤 디자인 **우수 졸업논문상 수상**
- **컴퓨터공학과 INLAB 학부 연구생** (2022.03 ~ 2022.11)
  - **Go & Docker 3-Tier 인프라 구축**: Go 언어 기반 커뮤니티 CRUD REST API 및 커스텀 CORS 미들웨어를 개발하고, `Nginx - Go WAS - MySQL` 컨테이너를 Docker Compose(`initdb.d` 스키마 자동화)로 오케스트레이션
  - **국제 의료 데이터 표준(HL7 FHIR) 및 AI 서비스 연동**: Hapi FHIR 표준 규격(`Patient`, `Encounter`, `Condition`, `Medication`) 기반 환자 진료·처방 기록(PHR) 파싱 대시보드(React/Express) 구현 및 탈모 예측 AI 모델 모바일(React Native) 서빙 파이프라인 구축
- **Certifications**: 정보처리기사, SQLD (SQL 개발자)

---

### 📫 Contact & Channels

- **Email**: [iamwotjr@gmail.com](mailto:iamwotjr@gmail.com)
- **GitHub**: [https://github.com/iamwotjr99](https://github.com/iamwotjr99)

---

### 📊 GitHub Stats

![Jaesuk's GitHub stats](https://github-readme-stats.vercel.app/api?username=iamwotjr99&show_icons=true&theme=default)
