# WorldJob Notice Notifier

월드잡플러스 공지사항 목록을 주기적으로 확인하여  
새로운 일반 공지가 등록되면 Discord로 알림을 보내는 Python 프로젝트입니다.

## Features

- 공지사항 목록 크롤링
- 최신 일반 공지 자동 추출
- 이전 공지와 비교하여 새 글 감지
- Discord Webhook 알림 전송
- SQLite 기반 상태 저장
- APScheduler 기반 주기 실행

## Tech Stack

- Python
- requests
- BeautifulSoup4
- SQLite
- APScheduler
- Discord Webhook

## Project Structure

```
new-post-notifier/
├── app.py
├── crawler.py
├── db.py
├── scheduler.py
├── notifier.py
├── config.py
├── requirements.txt
├── sites.json
└── README.md
```


## Setup

### 1. Create virtual environment

```
python -m venv .venv
```
### 2. Activate virtual environment

Windows

```
.venv\Scripts\activate
```

Mac / Linux

```
source .venv/bin/activate
```

### 3. Install dependencies

```
pip install -r requirements.txt
```

### 4. Set environment variable

Linux / Mac

```
export DISCORD_WEBHOOK_URL="your_webhook_url"
```

Windows PowerShell

```
$env:DISCORD_WEBHOOK_URL="your_webhook_url"
```

### 5. Run

```
python app.py
```

## How it works

1. 월드잡 공지사항 목록 페이지 요청
2. 일반 공지 중 최신 글 추출
3. DB에 저장된 이전 공지와 비교
4. 새 공지 발견 시 Discord 알림 전송

## Future Improvements

- 여러 사이트 지원
- FastAPI 기반 웹 UI
- Docker 배포
- GitHub Actions 자동 실행
