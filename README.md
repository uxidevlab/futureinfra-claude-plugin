# FutureInfra plugin for Claude Code

Deploy your project to **[FutureInfra](https://futureinfra.ai)** — a Korean cloud built for AI agents — by just saying *"deploy this"*.

One install gives Claude Code:

- **FutureInfra MCP server** (`https://futureinfra.ai/v1/mcp`) — create servers, deploy Docker apps with HTTPS URLs, manage domains, call 300+ AI models, and more.
- **`deploy` skill** — a step-by-step flow: pick App vs. server, show the price and wait for your OK, deploy, read logs and fix, then report the live URL.

## Install

```text
/plugin marketplace add uxidevlab/futureinfra-claude-plugin
/plugin install futureinfra@futureinfra
```

If adding the marketplace fails with an SSH/host-key error, use the HTTPS address instead:
`/plugin marketplace add https://github.com/uxidevlab/futureinfra-claude-plugin.git`

Then run `/mcp`, choose **futureinfra**, and sign in with your FutureInfra account in the browser (no API key needed). New accounts get free starter credit — sign up at [futureinfra.ai](https://futureinfra.ai).

## Try it

```text
deploy this project to FutureInfra
make a small server and install n8n
connect my domain example.com to this app
```

Claude always shows what it will create and the monthly price, and waits for your yes before creating anything.

---

## 한국어

**퓨쳐인프라** 클라우드에 Claude Code 로 "배포해줘" 한마디로 올리는 플러그인입니다.

설치하면 두 가지가 같이 들어옵니다.

- **퓨쳐인프라 MCP 연결** — 서버 만들기, 도커 앱 배포(HTTPS 주소 자동), 도메인, AI 모델 300여 종 호출 등
- **deploy 스킬** — 앱으로 올릴지 서버로 올릴지 고르고, 월 요금을 먼저 보여 주고 확인을 받은 뒤 배포, 오류는 로그를 읽고 고친 다음 주소를 알려 줍니다.

### 설치

```text
/plugin marketplace add uxidevlab/futureinfra-claude-plugin
/plugin install futureinfra@futureinfra
```

마켓플레이스 추가에서 SSH 오류가 나면 HTTPS 주소로 넣으세요: `/plugin marketplace add https://github.com/uxidevlab/futureinfra-claude-plugin.git`

설치 뒤 `/mcp` → **futureinfra** → 브라우저에서 퓨쳐인프라 계정으로 로그인하면 끝입니다(API 키 필요 없음). 계정은 [futureinfra.ai](https://futureinfra.ai) 에서 만들 수 있습니다.

### 이렇게 말해 보세요

```text
이 프로젝트 퓨쳐인프라에 배포해줘
작은 서버 하나 만들고 n8n 설치해줘
이 앱에 내 도메인 example.com 연결해줘
```

무엇을 만들지와 월 요금을 먼저 보여 주고, "네"라고 하기 전에는 아무것도 만들지 않습니다.

## Support

- Docs: https://futureinfra.ai/docs/
- Email: support@futureinfra.ai
