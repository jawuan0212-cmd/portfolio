# Project Portfolio

I build AI agent systems, trading infrastructure, and SaaS products — with a focus on connecting probabilistic AI layers to deterministic, auditable backends.

Source code for most of these projects is private. If you'd like a walkthrough or code samples, reach out via GitHub.

---

## The Agent Mesh

Four of these systems run as an interconnected mesh: trading, operations, security, and incident response talking to each other over a shared event bus — with human approval gates on anything that touches money.

### Aurum — Algorithmic Trading System
Multi-broker automated trading bot for gold, oil, and index futures. TradingView Pine Script strategies fire webhooks into a Python execution engine with a smart order router (OANDA, MetaTrader 5 via MetaApi, AMP Futures), trailing-stop management, daily-loss circuit breakers, margin-breach protection, position reconciliation, and a full trade journal. Includes a shadow-mode second bot for strategy comparison and extensive pytest coverage.
**Stack:** Python, FastAPI, Redis, Pine Script, OANDA / MetaApi / CQG APIs

### Hermes — Cross-Bot Operations Bus
Unified event bus connecting Aurum, CLAIRO, and Pisces. Broker outages automatically open incident triage runs; security blocks trigger investigation playbooks; completed remediations queue a trading resume that **requires explicit human confirmation via Telegram** before the bot trades again. Timeout escalation if no decision arrives.
**Stack:** Python, Redis, Telegram Bot API

### Pisces — Incident Triage & Remediation
Automated incident-response platform: playbook-driven triage runner with approval gates, Grafana observability dashboards, Helm chart for Kubernetes deployment, and CI via GitHub Actions.
**Stack:** Python, Grafana, Helm/Kubernetes, GitHub Actions

### CLAIRO (AutOps) — Operations Control Plane
AI operations control plane with a hash-chained audit log, authentication layer, prompt-injection firewall, and a React dashboard for oversight of automated actions.
**Stack:** Python, React/TypeScript, FastAPI

---

## Standalone Builds

### Circe — AI Sales Agent + Immutable Ledger
Two-layer FinOps loop: a LangGraph-powered B2B sales agent (prospecting → qualification → pricing → close) hands off to a Go financial ledger the moment a deal closes. The probabilistic layer never touches money directly — deposits are logged through an authenticated API into PostgreSQL with integer-cents amounts, an append-only audit log, and a database trigger enforcing immutability.
**Stack:** Python, LangGraph, FastAPI, Go, Gin, PostgreSQL, Docker Compose

### Fieldstone — Supply-Chain-Finance Gateway
Banking middleware gateway with idempotency-key passthrough, per-IP rate limiting, HashiCorp Vault AppRole authentication, and audited Kubernetes manifests.
**Stack:** Go, Kubernetes, HashiCorp Vault

### Titan Proxy — LLM Gateway
OpenAI-compatible streaming proxy: prompt compression, automatic model arbitrage (cheapest capable model wins), fail-open fallback to a secondary upstream, SHA-256-keyed response cache with SSE replay, sliding-window rate limiting, per-user spend caps, and Prometheus metrics.
**Stack:** Python, asyncpg/PostgreSQL, Docker, Prometheus

### ZeroFluff — Resume Bullet SaaS
Web app that rewrites resume bullets into quantified, recruiter-ready language — paste text or import straight from a GitHub repo. Stripe-powered checkout.
**Stack:** Next.js, TypeScript, Tailwind, Stripe, Vercel

---

## In Development

- **Helios** — enterprise AI platform (pitch/concept stage)
- **YT Automated** — YouTube content automation pipeline
- **Course** — video series on building these systems: agent memory, prompt-injection defense, why money belongs in integers, and full portfolio architecture breakdowns

---

## License

MIT — see [LICENSE](LICENSE)
