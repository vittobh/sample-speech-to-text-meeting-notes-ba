# Sample — Automated Meeting Notes (Speech-to-Text) BA Pack

Personal research sample from early BA work. Full BA pack for a feature embedding speech-to-text + automated email notes inside an existing video-conferencing product (telecom client, sanitized).

## What's inside
- Business Requirements Document (BRD)
- Competitor / open-market analysis (Speech-to-Text APIs)
- MSCW feature prioritization
- Functional + non-functional requirements
- User story + acceptance criteria
- Use-flow description

See [BRD.md](BRD.md).

## Highlights
- **Feasibility-led tech choice:** Google Cloud Speech-to-Text selected after ranked competitor analysis (Google · IBM Watson · Speech-to-Text API · Rev.AI)
- **MSCW prioritization** — Must / Should / Could / Won't tables for scope discipline
- **Production-grade NFRs** — security, 24×7 availability, peak-time perf, service-based architecture for future extension
- **Crisp user story + acceptance criteria** — Given / When / Then format, 30-min email-delivery SLO

## Today's lens
A modern take would replace one-shot Speech-to-Text with a multi-agent pipeline: live ASR → speaker diarization → action-item extraction (LLM) → calendar / CRM write-back, gated by an eval harness. See [vittobh/pm-os](https://github.com/vittobh/pm-os).

---
Author: **Vittobha Vignesh S** · License: MIT

---

## 🚀 Live Prototype
**[https://vittobh.github.io/sample-speech-to-text-meeting-notes-ba/](https://vittobh.github.io/sample-speech-to-text-meeting-notes-ba/)**

Working front-end with light + dark mode (toggle in header). Mock backend by default; add an Anthropic/Gemini/Grok key to browser localStorage to attempt live calls.

## 🤖 AI Use Cases (2026)
See **[AI_USE_CASES.md](AI_USE_CASES.md)** — agentic upgrade plan, OSS stack, concrete prompts, evals.

## ⚠️ Limitations
See **[LIMITATIONS.md](LIMITATIONS.md)** — what's mocked vs needs API keys / server proxy.
