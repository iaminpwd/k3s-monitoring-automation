깃허브 레포지토리의 얼굴이 될 **`README.md`** 초안을 작성해 드립니다. 이 내용은 사용자님이 겪었던 트러블슈팅 경험을 '기술적 역량'으로 승화시켜 기록한 것이 특징입니다.

이 내용을 복사해서 `ansible_project` 폴더의 **`README.md`** 파일에 덮어쓰기 하세요!

---

# 🚀 K3s Monitoring Automation Stack

앤서블(Ansible)을 활용하여 K3s 클러스터의 상태를 중앙 집중식으로 모니터링하는 인프라 자동화 프로젝트입니다. **Prometheus Remote Write** 아키텍처를 채택하여 에이전트와 서버를 분리한 효율적인 모니터링 환경을 구축했습니다.

## 🏗️ Architecture

본 프로젝트는 **Pull & Push 하이브리드 방식**을 사용하여 데이터 수집 효율을 극대화했습니다.

1. **K3s Node (Agent):** `Prometheus Agent` 모드로 작동하며 클러스터 내부 메트릭을 수집합니다.
2. **Monitoring Node (Server):** 중앙 프로메테우스 서버가 `Remote Write` 데이터를 수신하고 `Grafana`를 통해 시각화합니다.
3. **Ansible:** 전 과정을 코드로 자동화(IaC)하여 재현 가능한 인프라를 구축했습니다.

---

## 🛠 Tech Stack

* **Automation:** Ansible
* **Container:** Docker
* **Orchestration:** K3s (Kubernetes)
* **Monitoring:** Prometheus (Remote Write mode), Node Exporter
* **Visualization:** Grafana
* **Environment:** Vagrant, Ubuntu 22.04 LTS

---

## ✨ Key Features & Implementation

* **Remote Write Setup:** 중앙 서버의 부하를 줄이기 위해 에이전트 모드의 프로메테우스에서 데이터를 쏘아주는 방식 구현.
* **RBAC Hardening:** 에이전트 파드가 클러스터 자원을 안전하게 조회할 수 있도록 전용 `ServiceAccount` 및 `ClusterRole` 적용.
* **Containerized Monitoring:** Docker를 사용하여 프로메테우스 스택을 컨테이너화하고 데이터 영속성(Persistence) 확보.
