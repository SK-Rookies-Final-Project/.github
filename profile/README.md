# Confluent Kafka 무중단 클러스터링을 통한 실시간 위협 탑지 파이프라인 구축
> **SK Shieldus Rookies 3기 최종 프로젝트** (2025.07 ~ 2025.09)

## 📌 프로젝트 개요 및 배경

### 1. 프로젝트 개요
멀티 리전(Multi-Region) 아키텍처를 통해 운영 서버의 부하를 최소화하면서, 대규모 트래픽 속에서 발생하는 보안 위협(비정상 접근, 연속 인증 실패 등)을 실시간으로 탐지하고 시각화하는 데이터 파이프라인 구축 프로젝트입니다.

### 2. 기획 배경
* **초기 구상:** 대규모 데이터 흐름의 전체 상태를 모니터링하고, 병목이나 장애 발생 시 실시간으로 트러블슈팅할 수 있는 통합 솔루션을 기획했습니다.
* **목표 구체화:** 한정된 프로젝트 기간 내에 가장 완성도 높은 솔루션을 개발하기 위해, 가장 중요하다 생각되는 **'인증 및 인가 기반의 보안 위협 실시간 탐지'** 로 핵심 타겟을 좁혀 개발에 집중했습니다.

## 📊 전체 시스템 아키텍처 (System Architecture)

운영 환경(Seoul)의 부하를 방지하기 위해 분석 환경(Ohio)을 분리한 멀티 리전 아키텍처입니다. 발생한 Audit Log는 Kafka를 거쳐 Flink에서 실시간 처리되며, 최종적으로 React 대시보드를 통해 관리자에게 위협 알림이 전송됩니다.

<img width="1219" height="562" alt="Image" src="https://github.com/user-attachments/assets/839a3c2f-3afb-4078-8ad7-44fb12e38319" />

## 레포지토리 가이드(Repository Guide)

## 🛠️ 기술 스택 (Tech Stack)
- **Data Engineering:** Apache Kafka, Apache Flink
- **Backend / Frontend:** Java, Spring Boot, React, JavaScript
- **Infrastructure:** Firebase (프로토타입 배포)
- **Collaboration:** Git, Notion, Jira (Agile 프로세스)

## 💡 주요 성과 및 SE로서의 인사이트
- **클러스터 격리를 통한 가용성 확보:** 기존 운영 서버에 영향을 주지 않으면서 실시간 로그를 수집할 수 있는 아키텍처의 중요성 확인
- **가시성(Visibility) 제공의 가치:** 방대한 로그 데이터를 관리자가 직관적으로 대응할 수 있도록 대시보드로 번역해 내는 과정 경험
