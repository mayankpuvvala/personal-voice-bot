# Knowledge Base — Mayank Puvvala

Source of truth for the `vapi_assistant.json` facts block. Edit this file
first when anything changes, then copy the relevant parts into the
assistant's system prompt (Vapi doesn't read this file directly).

**Sources:**
- Resume: `Mayank_Puvvala_GenAI.pdf` (Downloads root) — treated as master
- GitHub: https://github.com/mayankpuvvala (fetched)
- Hugging Face: https://huggingface.co/mayankpuvvala (fetched)
- Medium: https://medium.com/@puvvalamayank (fetched)
- LinkedIn: https://www.linkedin.com/in/mayankpuvvala/ — **could not fetch**
  (LinkedIn blocks automated requests). Add manually below if you want its
  content included.
- LeetCode: https://leetcode.com/u/mayankpuvvala/ — **could not fetch** (403,
  LeetCode blocks automated requests). Add manually below if you want stats
  included.

---

## Contact
- Email: puvvalamayank@gmail.com
- Phone: +91-9014148879
- Location: Hyderabad, India
- GitHub: github.com/mayankpuvvala
- LinkedIn: linkedin.com/in/mayankpuvvala
- Medium: medium.com/@puvvalamayank
- Hugging Face: huggingface.co/mayankpuvvala
- LeetCode: leetcode.com/u/mayankpuvvala

## Career interests
Mayank is actively looking to move toward **voice AI, conversational AI, and LLM engineering roles** — his current TCS work is data/ML infrastructure, but his MindChords.AI experience (ElevenLabs TTS, Voiceflow, Botpress, cutting voice-response latency from 3.2s to 1.6s, production voice agents) and GenAI projects (RAG, LoRA fine-tuning) are the direction he wants to go next. If a caller raises a voice AI, conversational AI, or LLM/GenAI engineering opportunity, that's high-priority interest for him, even though it doesn't match his current day-to-day title.

## Work experience

# Current role
**Systems Engineer — Data & ML Infrastructure, Tata Consultancy Services**, Hyderabad — Feb 2026–Present
- Works on Vanguard's financial data infrastructure at TCS: manages data in S3 buckets, queries it via Amazon Athena.
- Leading the migration of Vanguard's financial data pipeline from Boomi to Microsoft Fabric — Boomi previously handled S3 ingestion and left data clean and now the fabric doesn't give clean so, we are processign the data as well, so part of the migration is cleaning/restructuring it in Fabric. Tracks and updates migration progress in Jira.
- Built automated migration scripts using Claude (Claude Code, session-based prompts) written in HQL (Hive Query Language) — cut down the time new joiners previously spent manually migrating data from the CRM into Fabric by hand. The scripts require confirmation at key steps and automatically check for drift (to catch if the automation goes off track / produces unexpected results), then post detailed results directly to Confluence so seniors can review the run without digging through logs.
- Broader team scope also touches AWS Glue, Apache Airflow, PySpark, Redshift, and RDS for ETL work on the same platform (per resume).

**Machine Learning Engineer, MindChords.AI** (Remote) — Sept 2025–Jan 2026
- Reduced voice response latency from 3.2s to 1.6s via async token streaming, selective audio-byte processing, and optimized inter-service communication.
- Improved LLM reliability using hybrid intent classification + rule-based fallback architecture, resolving 7+ critical failure patterns in production call flows.
- Designed integration layer connecting ElevenLabs (TTS), Voiceflow, and Botpress to orchestrate end-to-end conversational AI workflows, supporting 100+ concurrent voice sessions in production.
- Engineered fail-safe recovery for silent/inactive calls; built a YAML-driven analytics framework for configurable audio metric selection without code changes.

**Machine Learning Engineer Intern, Seyche Technologies** (Remote) — Nov 2023–Mar 2024
- Built NLP pipelines for text classification and sentiment analysis, enabling automated tagging and priority routing of support tickets.
- Developed a TF-IDF + RF Classifier intent module as the FAQ-routing backbone, replacing fully manual ticket triage for a support team handling 500+ daily queries.

## Education
**SRM Institute of Science & Technology**, Chennai — B.Tech in Computer Science, CGPA 9.12/10, 2021–2025

## Projects
**Financial RAG — SEC 10-K Question Answering** — Agentic RAG, Qdrant, Groq, FastAPI, fastembed (ONNX)
- Agentic RAG system that answers financial questions from real SEC 10-K filings with cited sources. A routing layer (Groq llama-3.1-8b) classifies each query — single-doc, multi-doc, temporal, or out-of-scope — then decomposes multi-doc/temporal questions into sub-queries before retrieval.
- Hybrid retrieval (dense BGE embeddings + BM25, RRF fusion, cross-encoder reranking) with parent-child chunking for precise retrieval and rich LLM context. Pre-indexed 35 filings across tech/banking/asset management; on-demand ingestion auto-resolves, fetches, and indexes any other SEC-listed company on the fly.
- Fully ONNX-based stack (fastembed, no PyTorch) to keep memory footprint low; deployed live on Railway. RAGAS-evaluated. GitHub: github.com/mayankpuvvala/Financial_RAG

**AI-Powered Compliance Risk Analyzer** — LangChain, Azure OpenAI, ChromaDB, FastAPI
- RAG system that ingests regulatory documents (PDF/TXT), chunks and embeds them in ChromaDB, and answers questions strictly grounded in the uploaded documents (no hallucination outside scope).
- Multi-document comparison layer detects similarities, differences, and conflicts across documents, extracts obligations/rules, and classifies compliance risks into Low/Medium/High severity.

**LLM Fine-Tuning for Structured Text Generation** — PyTorch, LoRA (PEFT), T5, Hugging Face, FastAPI
- Fine-tuned T5 with LoRA on a custom GitHub Issues dataset; ~50% ROUGE-F1. Deployed async FastAPI inference on Hugging Face Spaces.
- Model and dataset got 60+ downloads in the first week; pipeline documented in a public Medium post adopted by external developers.

**Multimodal Exam Proctoring System** — YOLOv11, MediaPipe, Librosa, OpenCV
- Real-time multi-modal proctoring system at 24 FPS using YOLOv11, MediaPipe gaze tracking, and STFT-based audio anomaly detection.
- 85% violation detection accuracy across simultaneous video, audio, and browser activity streams.

## Skills
- **ML & GenAI**: LLMs, RAG, Agentic RAG, LoRA/PEFT, Fine-tuning, Transformers, PyTorch, NLP, Computer Vision, Multimodal AI, UnSloth
- **Data & Cloud**: AWS (Glue, S3, Redshift, Lambda, DMS, ECS, CloudWatch), Airflow, PySpark, Kafka, SQL
- **Backend & Tools**: FastAPI, REST APIs, Async Systems, Docker, LangChain, LangGraph, RAGAS, ChromaDB, Qdrant, Groq, Hugging Face, Git

## Certifications & achievements
- Oracle Certified Generative AI Professional
- NPTEL: Machine Learning (Elite Batch) — IIIT Delhi
- Open-source T5 fine-tuning model & dataset: 60+ downloads in first week, adopted by external developers

## GitHub (github.com/mayankpuvvala)
Bio: Machine Learning Engineer specializing in audio, speech, and NLP systems; builds production-grade ML solutions including LLMs, RAG pipelines, and voice-driven agents. Location listed as Chennai.

Pinned repos:
- **100DaysOfML** (Jupyter Notebook) — deep dive into ML/DL with theory + code implementations
- **Exam-Proctoring-System** (Python) — computer vision project using head pose estimation, PnP algorithm, blur detection (earlier version of the Multimodal Exam Proctoring project above)
- **Lok_Sabha_Elections_2024___NLP** (Jupyter Notebook) — web scraping + NLP analysis
- **Grinding_Leetcode** (Python) — coding practice repo

## Hugging Face (huggingface.co/mayankpuvvala)
Spaces:
- **AI Content Detector** — analyze text to detect AI-generated content
- **Pytorch Issues Deployment** — generate detailed PyTorch issue reports
- **Spoken English Scoring** — transcribe, score, and correct spoken grammar
- **Resume Parser GenAI** — parse and score a resume against a job description

Models:
- **lora-t5-pytorch-issues**
- **peft_lora_t5_merged_model_pytorch_issues** (60.5M params, 23 downloads)

Datasets:
- **github-pytorch-issues** (10k items, 40 downloads)

## Medium (medium.com/@puvvalamayank)
- "Learning computer vision via projects" (Sep 19, 2024) — building an AI-powered exam monitoring system ("Watcher") for online proctoring
- "Real-World LLM Fine-Tuning: My Journey, Mistakes & Wins" (May 15, 2025) — fine-tuning and deployment experience
- "Resume Improver using Generative AI — My First Step into ML Production" (Apr 30, 2025) — deploying a GenAI pipeline to production
- "What I learnt from my first Kaggle Competition" (Nov 12, 2024)
- "#100DaysOfML" series (Dec 2023) — daily ML/DL learning log, e.g. neural nets from scratch, backprop, image generation, diffusion models

## LinkedIn — not fetched
Hello, I’m Mayank
Experienced in building production-level conversation AI applications for businesses. Now dabbling with Data Engineering with AWS solutions
I’m great at Machine Learning, Generative AI and Data Structures & Algorithms.



## LeetCode — not fetched
300+ problems with medium 170+ in it. 
