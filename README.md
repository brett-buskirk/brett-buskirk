# Brett Buskirk

Platform / DevOps engineer — cloud infrastructure, IaC, and full-stack delivery. I work
across AWS, GCP, and DigitalOcean; reach for Terraform + Ansible when I'm provisioning
and React or Astro when I'm shipping a frontend. Five years of shipping things that hold
up in production, now doing it independently.

Available for freelance engagements → **[brett-buskirk.dev](https://brett-buskirk.dev)**

![TypeScript](https://img.shields.io/badge/TypeScript-3178c6?logo=typescript&logoColor=fff&style=flat-square)
![Python](https://img.shields.io/badge/Python-3776ab?logo=python&logoColor=fff&style=flat-square)
![React](https://img.shields.io/badge/React-20232a?logo=react&logoColor=61dafb&style=flat-square)
![Node.js](https://img.shields.io/badge/Node.js-339933?logo=nodedotjs&logoColor=fff&style=flat-square)
![Terraform](https://img.shields.io/badge/Terraform-7b42bc?logo=terraform&logoColor=fff&style=flat-square)
![Ansible](https://img.shields.io/badge/Ansible-ee0000?logo=ansible&logoColor=fff&style=flat-square)
![Docker](https://img.shields.io/badge/Docker-2496ed?logo=docker&logoColor=fff&style=flat-square)
![AWS](https://img.shields.io/badge/AWS-232f3e?logo=amazonwebservices&logoColor=ff9900&style=flat-square)
![DigitalOcean](https://img.shields.io/badge/DigitalOcean-0080ff?logo=digitalocean&logoColor=fff&style=flat-square)
![Linux](https://img.shields.io/badge/Linux-1a1a1a?logo=linux&logoColor=fcc624&style=flat-square)

## What I work on

- **Cloud infrastructure** — VPC design, compute provisioning, firewall rules, zero-trust access via Tailscale ([heimdall](https://github.com/brett-buskirk/heimdall))
- **Observability stacks** — Prometheus · Grafana · Loki · Alertmanager, deployed via Ansible and Docker Compose
- **IaC & automation** — Terraform modules, Ansible roles [published on Galaxy](https://galaxy.ansible.com/ui/standalone/roles/brett-buskirk/do_network_routing/), Bash/Python tooling
- **CI/CD pipelines** — GitHub Actions from typecheck through build to cloud deploy ([day-one](https://github.com/brett-buskirk/day-one))
- **Agentic tooling** — guardrails and CI integration that keep AI coding agents shipping safe, reviewable work ([AgentGate](https://github.com/brett-buskirk/agent-gate) · [the story](https://brett-buskirk.medium.com/a-seatbelt-for-ai-generated-pull-requests-5f70d42f8a75))
- **Web apps** — React · TypeScript · Astro · Vite, from single-page tools to full GitOps deployments ([rc-journey-blog](https://github.com/brett-buskirk/rc-journey-blog))

## Stack

**Infrastructure:** Terraform · Ansible · Docker · Linux · Nginx  
**Cloud:** AWS · GCP · DigitalOcean  
**Languages:** TypeScript · JavaScript · Python · Bash · HCL  
**Web:** React · Astro · Vite · Node.js  
**Observability:** Prometheus · Grafana · Loki · Alertmanager · Tailscale

## 🛠️ Selected projects

| Project | What it is | Stack |
|---|---|---|
| **[AgentGate](https://github.com/brett-buskirk/agent-gate)** | CI guardrails for AI-agent pull requests — secrets, scope, missing tests, plus an opt-in LLM intent check. Listed on the [GitHub Marketplace](https://github.com/marketplace/actions/agentgate-ai-pr-guardrails). | TypeScript · GitHub Action · npm |
| **[claude-ticket-gen](https://www.npmjs.com/package/claude-gh-ticket-gen)** | AI CLI that parses roadmap docs and turns them into well-formed GitHub issues. | TypeScript · Claude API · npm |
| **[Ansible Galaxy roles](https://galaxy.ansible.com/ui/standalone/roles/brett-buskirk/do_network_routing/)** | Reusable roles for DigitalOcean networking, routing, and secure-user setup. | Ansible |
| **[Python network toolkit](https://github.com/brett-buskirk/python-network-toolkit)** | Packet sniffer, netcat, TCP/UDP clients & servers, SSH client/server — the wire, up close. | Python |
| **[Day One](https://dayone-sim.app)** | Reentry simulator PWA: live the first 90 days after release, one week at a time. | React · TypeScript · PWA |
| **[Go (圍棋)](https://brett-buskirk.github.io/go/)** | The ancient board game — full rules, territory scoring, and an MCTS opponent. Installable, offline. | Vanilla JS · PWA |

## Building with AI, responsibly

I build with AI coding agents — openly, and inside a system designed to keep it safe: no direct commits to `main`, every change gated by an automated review ([AgentGate](https://github.com/brett-buskirk/agent-gate)) **plus** a human sign-off, secret scanning, and signed, verified commits. The full policy → **[AI-DEVELOPMENT.md](AI-DEVELOPMENT.md)**.

---

<sub>Usually coding from somewhere off the grid — remote wilderness, good coffee, reliable internet. ☕</sub>
