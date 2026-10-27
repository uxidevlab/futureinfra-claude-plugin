---
name: deploy
description: Deploy the current project to FutureInfra (Korean cloud) — Docker apps with HTTPS URLs, full virtual servers, domains. Use when the user says "deploy this", "put this online", "host this", "make a server", "배포해줘", "서버에 올려줘", "서버 만들어줘", "도메인 연결해줘", or asks to run their app on FutureInfra.
---

# Deploy to FutureInfra

FutureInfra tools come from the `futureinfra` MCP server bundled with this plugin.
Tool names below are the MCP tool names; if a name is not found, call `fi_find_tools` with a short description of what you need.

## 0. Make sure the connection works
- Call `account_me`. If it fails with an auth error, tell the user to run `/mcp`, pick **futureinfra**, and sign in (browser login, no API key needed). Stop until they confirm.
- Call `account_orgs` and tell the user which organization will be billed. Switch with `account_switch_org` only if they ask.

## 1. Pick the right target (ask only if it is unclear)
| The project | Use |
|---|---|
| Has a `Dockerfile`, or is a web app/API that can run in one container | **App** — `apps_create` then `apps_deploy`. Gets an HTTPS URL automatically. |
| Needs SSH, several processes, a GPU, or the user says "server"/"VM" | **Virtual server** — `cloud_catalog` → `cloud_create_instance` |
| Popular open-source tool (n8n, WordPress, Dify, Open WebUI, Uptime Kuma, …) | **One-click template** — check `apps_create` options / `cloud_catalog` for a template first |
| Only wants a domain | `domain_search` |

Prefer an **App** for typical web projects — it is cheaper and has HTTPS without extra setup.

## 2. Confirm cost before creating anything
- Read prices from `cloud_catalog` (never guess numbers) and the balance from `billing_wallet`.
- Tell the user, in one or two lines: what will be created, the monthly price, and the organization. **Wait for a yes** before any create/deploy call. Deleting resources (`cloud_delete_instance`) also needs an explicit yes.

## 3. Deploy
**App path**
1. If there is no image registry, create a FutureInfra git repo: `git_create_repo` → `git_issue_credentials`, then `git push` the project (never print the credential; use it only in the push command).
2. `apps_create` (name, port the app listens on, env vars — put secrets in env, not in code), then `apps_deploy`.
3. Poll `apps_get` until it is running; on failure read `apps_logs` and fix the cause (wrong port and missing env vars are the usual ones), then redeploy.

**Server path**
1. `cloud_create_instance` with the smallest plan that fits; add the user's SSH public key if they have one.
2. Use `cloud_exec` to install and start the app, `cloud_open_port` for extra ports, `cloud_publish` to get an HTTPS address for a web port.

## 4. Report back
Give the user: the live URL, what was created (name/plan), the monthly price from the catalog, and how to update next time ("say *deploy again*"). Keep it short.

## Rules
- Never put API keys, passwords or tokens in code, commits, logs or chat. Use app env vars.
- Do not create more than one resource without asking.
- If something fails twice for the same reason, stop and explain the error in plain words instead of looping.
