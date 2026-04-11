# Confluent Kafka 무중단 클러스터링을 통한 실시간 위협 탑지 파이프라인 구축
> **SK Shieldus Rookies 3기 최종 프로젝트** (2025.07 ~ 2025.09)

<br>

## 📌 프로젝트 개요 및 배경

### 1. 프로젝트 개요
멀티 리전(Multi-Region) 아키텍처를 통해 운영 서버의 부하를 최소화하면서, 대규모 트래픽 속에서 발생하는 보안 위협(비정상 접근, 연속 인증 실패 등)을 실시간으로 탐지하고 시각화하는 데이터 파이프라인 구축 프로젝트입니다.

### 2. 기획 배경
* **초기 구상:** 대규모 데이터 흐름의 전체 상태를 모니터링하고, 병목이나 장애 발생 시 실시간으로 트러블슈팅할 수 있는 통합 솔루션을 기획했습니다.
* **목표 구체화:** 한정된 프로젝트 기간 내에 가장 완성도 높은 솔루션을 개발하기 위해, 가장 중요하다 생각되는 **'인증 및 인가 기반의 보안 위협 실시간 탐지'** 로 핵심 타겟을 좁혀 개발에 집중했습니다.

<br>
<br>

## 📊 전체 시스템 아키텍처 (System Architecture)

운영 환경(Seoul)의 부하를 방지하기 위해 분석 환경(Ohio)을 분리한 멀티 리전 아키텍처입니다. 발생한 Audit Log는 Kafka를 거쳐 Flink에서 실시간 처리되며, 최종적으로 React 대시보드를 통해 관리자에게 위협 알림이 전송됩니다.

<img width="1219" height="562" alt="Image" src="https://github.com/user-attachments/assets/839a3c2f-3afb-4078-8ad7-44fb12e38319" />

<br>
<br>

## 🔍레포지토리 가이드(Repository Guide)
* **Infra & DevOps:** `Terraform`/`Terraform_MDS`/`ansible`
* **Data Generate & Flink:** `AccessToSeoul`/`Producer`/`Flink`
* **DashBoard(Backend, Frontend):** `Backend`/`ReactFrontend`


<br>
<br>

## 🖥️ 대시보드 스크린샷 (DashBoard Screenshots)
운영환경과 연동하여 관리자가 실시간으로 위협을 인지하고 클러스터를 제어할 수 있도록 구현한 웹 대시보드 입니다.

### 모니터링 메인 화면
<img width="616" height="240" alt="Image" src="https://github.com/user-attachments/assets/9854ac8d-4969-4189-9a0f-93ae2eb99b8c" />

<br>

### 핵심 기능 상세
| 실시간 감사 모니터링 (위협 탐지) | 과거 데이터 이력 조회 및 통계 |
| :---: | :---: |
| <img width="447" height="308" alt="Image" src="https://github.com/user-attachments/assets/1ee24e12-8533-4b1b-80c1-ff7dc0a775e9" /> | <img width="485" height="286" alt="Image" src="https://github.com/user-attachments/assets/d7bccab0-33e5-4249-951a-4e5ec7a81a1a" /> |
| **비정상 접근 및 인증 실패 실시간 로그**<br>IP, 사용자, 접근 제어(거부) 상태 실시간 추적 | **기간별 위협 발생 통계 및 필터링**<br>Rapid Successive Attempts 등 패턴별 위협 분석 |

| Kafka 시스템 모니터링(Prometheus) | Kafka 클러스터 및 토픽 관리 |
| :---: | :---: |
| <img width="492" height="329" alt="Image" src="https://github.com/user-attachments/assets/81ed6cc1-5e67-4860-9a1c-4f4ed7ce3338" /> | <img width="472" height="356" alt="Image" src="https://github.com/user-attachments/assets/64b85c39-8710-4cbd-a57e-646140ea13fb" /> |
| **Prometheus 연동 컴포넌트 상태 확인**<br>Broker, Schema Registry등 Health Check | **브로커 상태 및 신규 토픽 제어**<br>클러스터 ID 확인 및 파티션/복제본(Replica) 설정 |
