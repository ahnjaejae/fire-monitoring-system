# 🔥 Fire & Environmental Monitoring System

**Raspberry Pi 5 + Hailo-8 + Arduino + FastAPI + WebSocket + MQTT + Docker + Grafana + Oracle Cloud 기반**  
실시간 화재 감지 및 환경 데이터 모니터링 통합 시스템

---

## 🧠 프로젝트 개요

이 시스템은 다음 기능을 제공합니다:

- **YOLO + Hailo-8 기반 화재 감지** (카메라 입력 실시간 처리)
- **Arduino 센서 데이터 수집** (온습도, 조도, CO2, 먼지 등)
- **FastAPI + MQTT + WebSocket 기반 데이터 처리 서버**
- **Grafana 대시보드 시각화**
- **Oracle Cloud에 자동 배포**
- **HTTPS 도메인 제공 (Caddy 서버 + Let's Encrypt)**

---

## 📦 시스템 구성도

```
[ Arduino Sensors ] --> [ Serial → FastAPI MQTT/WebSocket Server ] --> [ Grafana Dashboard ]
                               ↑
[ Camera + Hailo-8 ] ----------|
```

---

## ⚙️ 기술 스택

| 구성 요소     | 설명 |
|---------------|------|
| Raspberry Pi 5 | 엣지 디바이스, 라즈비안 64bit (Bookworm) 사용 |
| Hailo-8        | YOLO 기반 화재 감지, DeGirum SDK 활용 |
| Arduino        | 온습도/먼지/조도/CO2 센서 데이터 송신 |
| FastAPI        | API 서버 및 WebSocket 처리 |
| MQTT           | 센서 데이터 브로커 |
| WebSocket      | 실시간 전송 |
| Grafana        | 대시보드 시각화 |
| Caddy          | HTTPS 적용 및 도메인 처리 |
| Oracle Cloud   | 서버 배포 대상 |
| Docker         | 전체 컨테이너 통합 배포 |
| GitHub Actions | CI/CD 자동화 워크플로우 |

---

## 📁 디렉토리 구조

```
fire-monitoring-template/
├── backend/
│   ├── main.py
│   ├── mqtt_handler.py
│   ├── websocket.py
├── frontend/
│   └── static/index.html
├── hailo_inference/
│   └── hailo_fire_detect.py
├── sensors/
│   └── serial_reader.py
├── grafana/
│   └── dashboard.json
├── caddy/
│   └── Caddyfile
├── .github/
│   └── workflows/deploy.yml
├── docker-compose.yml
├── requirements.txt
├── LICENSE
└── README.md
```

---

## 🚀 빠른 시작

### 1. 의존성 설치

```bash
cd fire-monitoring-template
pip install -r requirements.txt
```

### 2. 서버 실행 (FastAPI)

```bash
uvicorn backend.main:app --reload --host 0.0.0.0 --port 8000
```

### 3. Arduino 센서 스크립트 실행

```bash
python sensors/serial_reader.py
```

### 4. Hailo 화재 감지 실행

```bash
python hailo_inference/hailo_fire_detect.py
```

### 5. Grafana 대시보드 설정

- `grafana/dashboard.json`을 Grafana에서 Import
- InfluxDB 등 데이터소스 연결 필요 시 config 수정

---

## 🌐 배포 방법

### Docker + docker-compose

```bash
docker-compose up --build
```

### GitHub Actions + Oracle Cloud

`.github/workflows/deploy.yml` 자동 워크플로우 참고

---

## 🛡️ 라이선스

본 프로젝트는 [MIT License](./LICENSE)를 따릅니다.

이 프로젝트는 [boraisik/Hailo8-Fire-Detection-with-DeGirum](https://github.com/boraisik/Hailo8-Fire-Detection-with-DeGirum)의 일부 코드를 참고했습니다.

---

## 👤 제작자

- GitHub: [ahnjaejae](https://github.com/ahnjaejae)
- Email: ahn@example.com

---