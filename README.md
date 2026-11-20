# Personal Voice Bot — Mayank Puvvala

**Live demo:** https://mayankpuvvala.github.io/personal-voice-bot/

A browser voice assistant that answers questions about my background (experience, skills, projects) and takes a message when it should not invent an answer.

Built as a portfolio demo of the same patterns I use in production voice agents: grounded facts, clear “I’m an AI assistant” framing, and a clean handoff when human follow-up is needed.

---

## Why this exists

Recruiters and hiring managers can **talk to the bot** instead of only reading a PDF:

- What I’ve shipped (RAG, voice agents, fine-tuning)
- Links to live demos and GitHub
- Leave name + contact + opportunity for me to follow up

---

## How it works (high level)

1. Facts live in a single knowledge source (resume + public profiles).
2. The assistant answers only from that block — no free-form biography invention.
3. Unknown / sensitive asks → take a message rather than guess.

Related production work:

- [voice_pipecat](https://github.com/mayankpuvvala/voice_pipecat) — Hinglish phone receptionist (Pipecat, telephony, evals)
- [voice_agents](https://github.com/mayankpuvvala/voice_agents) — browser receptionist with dashboard
- [Financial_RAG](https://github.com/mayankpuvvala/Financial_RAG) — agentic SEC Q&A (live)

---

## Stack

Vapi / n8n-style orchestration patterns · facts from master resume · static site on GitHub Pages

---

## Author

**Mayank Puvvala** — ML / LLM Application Engineer (Hyderabad)  
[LinkedIn](https://www.linkedin.com/in/mayankpuvvala/) · [GitHub](https://github.com/mayankpuvvala) · [Email](mailto:puvvalamayank@gmail.com)
