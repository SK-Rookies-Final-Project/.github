# 🛡️ 실시간 보안 위협 탐지 및 관리자 모니터링 파이프라인

## 📌 프로젝트 개요
운영 환경의 부하를 최소화하면서, 대규모 트래픽 속에서 발생하는 보안 위협(비정상 접근, 연속 인증 실패 등)을 실시간으로 탐지하고 시각화하는 데이터 파이프라인 구축 프로젝트입니다.

## ⚙️ 아키텍처 및 데이터 흐름 (Data Flow)
1. **[Data Source]** 운영 서버(Region 1)에서 발생하는 접근 로그 데이터
2. **[Message Queue]** **Apache Kafka**를 통해 운영 환경과 분석 환경(Region 2)을 격리하여 데이터 유실 및 부하 방지
3. **[Stream Processing]** **Apache Flink**의 Time Window 함수를 활용하여 1초 단위의 실시간 이상 징후 분석 및 분류
4. **[Visualization]** **Spring Boot** 백엔드를 거쳐 **React** 기반 관리자 대시보드에 실시간 위협 알림 제공

## 🛠️ 기술 스택 (Tech Stack)
- **Data Engineering:** Apache Kafka, Apache Flink
- **Backend / Frontend:** Java, Spring Boot, React, JavaScript
- **Infrastructure:** Firebase (프로토타입 배포)
- **Collaboration:** Git, Notion, Jira (Agile 프로세스)

## 💡 주요 성과 및 SE로서의 인사이트
- **클러스터 격리를 통한 가용성 확보:** 기존 운영 서버에 영향을 주지 않으면서 실시간 로그를 수집할 수 있는 아키텍처의 중요성 확인
- **가시성(Visibility) 제공의 가치:** 방대한 로그 데이터를 관리자가 직관적으로 대응할 수 있도록 대시보드로 번역해 내는 과정 경험
