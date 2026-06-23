<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=26&duration=3000&pause=1000&color=58A6FF&center=true&vCenter=true&repeat=true&width=750&height=70&lines=Senior+Software+Engineer+%7C+5+years;Distributed+Systems+%2F+Polyglot+Microservices;Fintech+%26+Loyalty+Platform+Architect;On-prem+AI+Engineering+on+Bare+Metal)](https://git.io/typing-svg)

[![Portfolio](https://img.shields.io/badge/Portfolio-suvodeepdas.com-58A6FF?style=flat-square&logo=googlechrome&logoColor=white)](https://suvodeepdas.com)
[![RewardSync](https://img.shields.io/badge/Live_Project-RewardSync-00C896?style=flat-square&logo=amazonaws&logoColor=white)](https://rewardsync.suvodeepdas.com)
[![npm](https://img.shields.io/badge/npm-react--native--vg--retailer--sdk-CB3837?style=flat-square&logo=npm&logoColor=white)](https://www.npmjs.com/package/react-native-vg-retailer-sdk)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/suvodeep-das-06374489/)
[![Medium](https://img.shields.io/badge/Medium-Writing-12100E?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@suvodeep4119)

</div>

---

## Hey, I'm Suvodeep

Senior Software Engineer — backend systems, distributed architecture, and loyalty/fintech platforms. Five years owning production systems end-to-end across M2P Fintech and V-Guard Rishta.

I'm the kind of engineer who doesn't just build the feature — I also find the GPU crash bug, the nginx timeout the upgrade exposed, and the circuit breaker that was silently wrong for a year. All in the same session.

---

## 🔧 What I'm Building

### [RewardSync](https://rewardsync.suvodeepdas.com) — Distributed Loyalty Engine
> Live · Self-hosted on bare metal · 6 polyglot microservices · No cloud, no managed services

```
Retailer's app
     │ HTTPS
     ▼
API Gateway (NestJS) ── auth, rate-limit, circuit-breaker, distributed tracing
     │
     ├── Identity   (NestJS)     — JWT auth, 15min access / 7day refresh tokens
     ├── Commerce   (Spring Boot)— QR scan processing, async point crediting via RabbitMQ
     ├── Rewards    (Spring Boot)— points wallet, tier engine, Redis-cached balance reads
     ├── Fraud      (FastAPI)    — 6-rule stateless scoring, Redis-only state, <100ms
     └── Recommendation (NestJS) — on-prem LLM inference, graceful fallback, source-tagged
```

**Numbers that are real, not estimated:**

| Metric | Value |
|---|---|
| Commerce scan response | **<50ms** (async RabbitMQ — no blocking on wallet credit) |
| Fraud scoring latency | **<100ms** across 6 weighted Redis rules |
| Redis SETNX dedup window | **24h** per QR/retailer pair — 409 on duplicate, no DB query |
| Seeded test transactions | **2 million** across all services |
| LLM inference | **llama3.2:3b via Ollama** — 27–47s on CPU, graceful fallback on any failure |

---

## 🖥️ The Infra Story — Running Production on a 2014 Laptop

**Hardware:** HP Pavilion 15 · Intel i3-4030U @ 1.90GHz (4 threads) · 11GB RAM + 4GB swap · ~931GB spinning HDD · Ubuntu 25.10 · Cloudflare Tunnel

What that box is running right now: 6 Docker containers (full RewardSync platform) + 5 independent Postgres databases + Redis + RabbitMQ + pgAdmin + Ollama running llama3.2:3b + Nginx reverse-proxying 5 live public domains. No cloud spend, no managed services.

**Why this matters — the model evaluation I actually ran:**

| Model | Disk | Latency | Verdict |
|---|---|---|---|
| tinyllama | 637MB | fast | Inconsistent — ignores "exactly 3" in 40% of runs |
| llama3.2:1b | 1.3GB | ~30s | Malformed JSON, hallucinated products |
| **llama3.2:3b** ✅ | 2.0GB | 27–47s | Clean JSON, 3 items, on-catalog branded products |
| qwen2.5:3b | 1.9GB | 20–30s | Valid format, but echoes category name as product |
| qwen2.5:7b | 4.7GB | **~298s** | Pushed box to 2.6GB swap — unusable on this hardware |

Upgrading from tinyllama → llama3.2:3b surfaced **3 production bugs** found and fixed in one session:

- **GPU crash** — NVIDIA 830M (2GB VRAM) segfaults on Ollama layer offload → fixed with `"num_gpu": 0` (CPU-only inference)
- **nginx 504** — default 60s `proxy_read_timeout` cut the response at exactly 60.6s → extended `/recommendation/` location block to 70s
- **Circuit breaker** — single hardcoded `REQUEST_TIMEOUT_MS = 5000` applied to all services including the LLM path → rebuilt to per-service config (recommendation: 65s; fast DB-backed services: 5s unchanged — surgical, not a global loosening)

---

## 🚀 Production Work

**V-Guard Rishta · Evolve Brands India** _(present)_

Sole engineer owning 4 production React Native apps, a .NET portal, and a SQL Server 2019 database — scope typically requiring a 3-person team.

- Published **[react-native-vg-retailer-sdk](https://www.npmjs.com/package/react-native-vg-retailer-sdk)** on npm — native Android (Kotlin) + iOS (Swift) SDK
- Shrunk a **55 GB SQL Server transaction log → 1 GB** via VLF consolidation, restoring 99.9% uptime
- Diagnosed and resolved a **207-session stored procedure blocking chain** under live production traffic
- Architected a T-1 OLTP→OLAP reporting DB with nightly seed scripts, incremental intraday loads, and a reporting queue to eliminate peak-hour lock contention

**M2P Fintech** _(2020–2023)_

- Built API throttling in Go + Node.js to process **100K+ CSV records per batch** — hours → minutes
- Launched a multi-tenant fintech backend (KeyCloak, MongoDB, Redis) from scratch through 2 acquisitions with zero SLA breaches

---

## 🛠️ Stack I Actually Use in Production

**Backend**

![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)

**Databases & Messaging**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=flat-square&logo=rabbitmq&logoColor=white)

**Mobile & SDK**

![React Native](https://img.shields.io/badge/React_Native-61DAFB?style=flat-square&logo=react&logoColor=black)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Swift](https://img.shields.io/badge/Swift-FA7343?style=flat-square&logo=swift&logoColor=white)

**Infrastructure & AI**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS_EC2-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu_25.10-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare_Tunnel-F38020?style=flat-square&logo=cloudflare&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-llama3.2:3b-black?style=flat-square&logo=meta&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-in_progress-4169E1?style=flat-square&logo=postgresql&logoColor=white)

---

## 🌐 Live Infrastructure on Loki

| Domain | What it is |
|---|---|
| [suvodeepdas.com](https://suvodeepdas.com) | Personal site |
| [rewardsync.suvodeepdas.com](https://rewardsync.suvodeepdas.com) | Live distributed loyalty engine + API docs |
| [portfolio.suvodeepdas.com](https://portfolio.suvodeepdas.com) | Angular portfolio (SPA) |
| [status.suvodeepdas.com](https://status.suvodeepdas.com) | Live visitor counter — per-domain, per-page, anonymized device breakdown |

All four public hostnames served from one Cloudflare Tunnel → Nginx → Docker stack on a laptop under my desk.

---

## 📄 Published Research

**[Traffic Signal Automation via Deep Learning](https://www.ijrece.org/)** · IJRECE Vol. 7 Issue 1 · ISSN 2393-9028 · 2019  
Real-time adaptive traffic signal control using a CNN architecture — published during MCA final year.

---

## ✍️ Writing

- [From Templating Engines to REST APIs — The Transition](https://medium.com/@suvodeep4119/from-templating-engines-to-rest-apis-the-transition-74d2afeee329)
- [Firewall Port Manipulation in AWS EC2 via PowerShell](https://medium.com/tensult/remotely-open-close-firewall-ports-in-ec2-managed-instance-using-powershell-scripts-4d6284ee68eb)

---

## 📊 GitHub Stats

<div align="center">

[![GitHub Stats](https://github-readme-stats.vercel.app/api?username=suvodeep4119&show_icons=true&theme=github_dark&hide_border=true&include_all_commits=true&count_private=true)](https://github.com/suvodeep4119)
&nbsp;
[![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=suvodeep4119&layout=compact&theme=github_dark&hide_border=true&langs_count=8)](https://github.com/suvodeep4119)

</div>

---

## 2026

Deepening distributed systems and applied AI engineering — specifically: agent orchestration and MCP tool design, LLM eval harness design, production safety patterns (guardrails, least-privilege, shadow-mode model rollout), and RAG pipelines over structured data.

---

<div align="center">

[![Portfolio](https://img.shields.io/badge/suvodeepdas.com-Visit-58A6FF?style=for-the-badge&logo=googlechrome&logoColor=white)](https://suvodeepdas.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/suvodeep-das-06374489/)
[![Stack Overflow](https://img.shields.io/badge/Stack_Overflow-Profile-F58025?style=for-the-badge&logo=stackoverflow&logoColor=white)](https://stackoverflow.com/users/10604369/1dx)
[![npm](https://img.shields.io/badge/npm-Package-CB3837?style=for-the-badge&logo=npm&logoColor=white)](https://www.npmjs.com/package/react-native-vg-retailer-sdk)

</div>
