# WorldJob Notice Notifier

월드잡플러스(WorldJob+) 공지사항을 주기적으로 확인하여  
새로운 일반 공지가 등록되면 Discord로 알림을 보내는 Python 기반 자동화 프로젝트입니다.

이 프로젝트는 단순 크롤러가 아니라 서버에 배포되어 24시간 동작하는 알림 시스템으로 설계되었습니다.

---

## Features

- 월드잡플러스 공지사항 목록 크롤링
- 최신 일반 공지 자동 추출
- 이전 공지와 비교하여 새 글 감지
- Discord Webhook 알림 전송
- SQLite 기반 상태 저장
- APScheduler 기반 주기 실행
- .env 기반 환경변수 설정
- Oracle Cloud VM 배포
- systemd 기반 24시간 운영

---

## Tech Stack

### Backend
Python

### Libraries

- requests
- BeautifulSoup4
- APScheduler
- python-dotenv

### Storage
SQLite

### Deployment

- Oracle Cloud Always Free VM
- systemd service

---

## Project Structure

```text
worldjob-notice-notifier/
├── app.py
├── crawler.py
├── db.py
├── scheduler.py
├── notifier.py
├── config.py
├── requirements.txt
├── sites.json
├── .env.example
└── README.md
```

---

## Setup (Local Development)

### 1. Create virtual environment

```bash
python -m venv .venv
```

### 2. Activate virtual environment

#### Windows

```bash
.venv\Scripts\activate
```

#### Mac / Linux

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Environment Variables

프로젝트 루트에 `.env` 파일을 생성합니다.

Example:

```env
DISCORD_WEBHOOK_URL=your_discord_webhook_url
CHECK_INTERVAL_MINUTES=10
```

설명

| Variable | Description |
|---|---|
| DISCORD_WEBHOOK_URL | Discord webhook URL for notifications |
| CHECK_INTERVAL_MINUTES | 공지 확인 주기 (분) |

---

## Run

```bash
python app.py
```

정상 실행 시:

```text
스케줄러 시작: 10분마다 점검
[CHECK] 사이트 점검 시작
```

---

## How it works

동작 흐름

1. 월드잡 공지사항 목록 페이지 요청
2. 일반 공지 중 최신 글 추출
3. DB에 저장된 이전 공지와 비교
4. 새 공지 발견 시 Discord Webhook으로 알림 전송
5. 상태를 SQLite DB에 저장

---

## Deployment (Oracle Cloud)

이 프로젝트는 Oracle Cloud Always Free VM에 배포되어 24시간 실행됩니다.

### Environment

- Oracle Linux 9
- Python 3
- systemd service

---

### 서비스 관리

```bash
sudo systemctl status worldjob-notifier
sudo systemctl restart worldjob-notifier
sudo systemctl stop worldjob-notifier
```

### 로그 확인

```bash
journalctl -u worldjob-notifier -f
```

---

## Future Improvements

- 여러 사이트 공지 모니터링
- FastAPI 기반 상태 API
- 웹 대시보드
- Docker 배포
- GitHub Actions 기반 자동 배포

---

## Author

GitHub  
https://github.com/cbssmh

---
