# FinEdu-Backend
클라우드 시스템 2024-2 프로젝트: Cloud native educational finance platform | Backend Repository

## FinEdu AI 소개
- OpenAI API를 사용하여 AI 기반의 뉴스 요약 및 학습 서비스 제공
- Docker를 활용하여 환경 동일성과 배포 용이
- Kubernetes의 오토스케일링 기능을 활용하여 시장 급변동 시에도 중단 없는 서비스 보장

### 서비스 화면
<img width="597" alt="Screenshot 2025-01-18 at 3 39 52 PM" src="https://github.com/user-attachments/assets/eee554ff-1ae8-4776-834b-7b8f4af94f53" /> <img width="533" alt="Screenshot 2025-01-18 at 3 40 46 PM" src="https://github.com/user-attachments/assets/06cf1a20-efe7-42b6-a982-899bbaae7fce" />

### 동작 시나리오
1. 주식 시장 급변동으로 인한 뉴스 폭증 대응 ➡️ 자동으로 요약 Pod 수를 늘려 요청을 빠르게 처리
2. 사용자의 요청 처리와 부하 분산 (로드밸런싱) ➡️ 트래픽을 Pod들에 균등하게 분산하여 처리 속도 유지
3. 데이터 백업 및 볼륨 관리 (데이터 안전성) ➡️ MySQL 데이터를 PersistentVolume에 저장하여 컨테이너 재시작이나 장애 발생 시에도 데이터 손실 없이 복구

### 프로젝트 구조
```
fineduai/ 
├── frontend/ # Frontend repo 
├── crawler/ # Crawler repo 
├── backend/ # Backend repo 
│ ├── common/ # 공동 모듈
│ ├── summarizer/ # 요약본 모듈
│ ├── quiz/ # 퀴즈 모듈
└── kubernetes/ # Kubernetes manifests 
  ├── mysql/ 
  │ ├── mysql-pv.yaml 
  │ ├── mysql-pvc.yaml 
  │ ├── mysql-deployment.yaml 
  │ └── mysql-service.yaml 
  ├── crawler/ 
  │ ├── crawler-deployment.yaml 
  │ ├── crawler-service.yaml 
  │ └── crawler-cronjob.yaml 
  ├── summarizer/ 
  │ ├── summarizer-deployment.yaml 
  │ └── summarizer-service.yaml 
  ├── quiz/ 
  │ ├── quiz-deployment.yaml 
  │ └── quiz-service.yaml 
  └── frontend/ 
    ├── frontend-deployment.yaml 
    └── frontend-service.yaml
```
