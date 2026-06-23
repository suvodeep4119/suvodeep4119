### Hey, I'm Suvodeep (1Dx)

**Senior Software Engineer** — backend systems, distributed architecture, and loyalty/fintech platforms.  
Five years owning production systems end-to-end — APIs, databases, mobile apps, and infrastructure — across M2P Fintech and V-Guard Rishta at Evolve Brands India.

---

### What I'm building

**[RewardSync](https://rewardsync.suvodeepdas.com)** — a polyglot distributed loyalty engine, self-hosted on bare-metal Ubuntu  
`NestJS · Spring Boot · FastAPI · PostgreSQL · Redis · RabbitMQ · Docker · Ollama/TinyLlama · Cloudflare Tunnel`

- Commerce scan response **<50ms** via async RabbitMQ point crediting
- Sub-100ms fraud detection across 6 weighted Redis rules with Redis SETNX dedup
- On-prem LLM inference (TinyLlama via Ollama) with eval harness, schema-validated output, and env-flag kill switch
- MCP server exposing wallet, scan-history, and fraud-score as agent tools
- RAG pipeline over retailer transaction history — pgvector + TinyLlama
- Isolation Forest fraud model running in shadow mode alongside the rules engine

---

### Production work

- Sole engineer owning **4 React Native apps**, a .NET portal, and a SQL Server database at V-Guard Rishta — scope typically requiring a 3-person team
- Published **[react-native-vg-retailer-sdk](https://www.npmjs.com/package/react-native-vg-retailer-sdk)** on npm — native Android (Kotlin) + iOS (Swift) SDK
- Shrunk a 55 GB SQL Server transaction log → 1 GB via VLF consolidation, restoring 99.9% uptime
- Diagnosed and resolved a 207-session stored procedure blocking chain in production under live traffic
- Built API throttling in Go + Node.js to process **100K+ CSV records per batch** at M2P Fintech

---

### Stack I actually use in production

**Backend:** Node.js · TypeScript · NestJS · Spring Boot · FastAPI · Go  
**Databases:** SQL Server 2019 · PostgreSQL · MongoDB · Redis  
**Messaging:** RabbitMQ  
**Mobile:** React Native (Android + iOS)  
**Infra:** AWS EC2 · Docker · Cloudflare Tunnel · Ubuntu Server  
**AI/ML:** Ollama · TinyLlama · pgvector · Isolation Forest · MCP

---

### Home server — loki

HP Pavilion running Ubuntu, self-hosting RewardSync and personal projects via Cloudflare Tunnel.  
Portfolio: [suvodeepdas.com](https://www.suvodeepdas.com)

---

### Published research

[Traffic Signal Automation via Deep Learning](https://www.ijrece.org/) · IJRECE Vol. 7 Issue 1, 2019  
Real-time adaptive traffic signal control using a CNN architecture — published during MCA final year.

---

### Writing

- [From Templating Engines to REST APIs — The Transition](https://medium.com/@suvodeep4119/from-templating-engines-to-rest-apis-the-transition-74d2afeee329)
- [Firewall Port Manipulation in AWS EC2 via PowerShell](https://medium.com/tensult/remotely-open-close-firewall-ports-in-ec2-managed-instance-using-powershell-scripts-4d6284ee68eb)

---

### 2026

Deepening distributed systems and applied AI engineering. Specifically: agent orchestration, LLM eval design, and production safety patterns (guardrails, least-privilege tool design, shadow-mode model rollout).

---

[Portfolio](https://www.suvodeepdas.com) · [LinkedIn](https://www.linkedin.com/in/suvodeep-das-06374489/) · [Stack Overflow](https://stackoverflow.com/users/10604369/1dx) · [npm](https://www.npmjs.com/package/react-native-vg-retailer-sdk) · [Medium](https://medium.com/@suvodeep4119)
