# Hi, I'm Daniel 👋

**AI Engineer** based in South Korea 🇰🇷, building LLM systems that are grounded, evaluated, and safe to put in front of users: RAG, tool-using agents, and the engineering around them (APIs, tests, CI, deployment).

I care about the unglamorous parts that decide whether an AI system can be trusted: retrieval that cites its sources, agents whose tools do real work, and responses that say when they *don't* know.

---

## 🔭 Featured projects

### [Aegis](https://github.com/dojedaro/aegis): AI compliance operations platform · [live demo](https://aegis-web-xi.vercel.app/)
Compliance review for GDPR, eIDAS 2.0, AML and the EU AI Act. A Claude agent uses tools that do real work: regulation retrieval (BM25), deterministic PII scanning, and finding recording that rejects citations to articles that don't exist. Explainable rule-based KYC risk scoring, an RBAC-protected audit trail, and 75 tests.
`TypeScript` `Express` `Claude tool use` `RAG` `JWT/RBAC` `Vitest`

### [Say What?](https://github.com/dojedaro/say-what): multilingual video Q&A with grounded RAG
Transcribes, translates and indexes YouTube/TikTok/Instagram videos, then answers questions in English, Spanish or Korean with timestamped citations. It refuses to answer when retrieval finds nothing relevant. One interface for OpenAI, Claude, Gemini and Azure.
`Python` `FastAPI` `ChromaDB` `Whisper` `pytest` `Docker`

### [MCP-TRADI-WIN](https://github.com/dojedaro/Tradi-Win-Explainable-Trading-Agents): explainable multi-agent trading (Master's thesis)
A multi-agent crypto forecasting framework combining time-series models and sentiment analysis under the Model Context Protocol. LLMs are used strictly for *explanation*, never for the trading decision itself.
`Multi-agent` `MCP` `Time series` `Explainable AI`

### [Research Paper RAG](https://github.com/dojedaro/research-paper-rag-qa-system): Q&A over academic papers
RAG with strict source grounding, conversation memory, retriever benchmarking and quantitative evaluation, served via Streamlit.
`RAG` `Evaluation` `Streamlit`

### [QLoRA fine-tuning](https://github.com/dojedaro/qlora-bert-sentiment-classification): parameter-efficient BERT
4-bit NF4 quantization with LoRA adapters for sentiment classification on limited hardware, with experiment tracking in W&B.
`PEFT` `QLoRA` `bitsandbytes` `Hugging Face`

### [LangGraph competitive-intelligence agent](https://github.com/dojedaro/langgraph-competitive-intelligence-agent)
An agentic workflow that discovers retail competitors via the Google Places API, estimates footfall patterns, and writes investor-ready reports.
`LangGraph` `Agents` `Tool integration`

<details>
<summary><b>More work</b>: RAG series, multimodal, audio ML, classical ML</summary>

**RAG techniques series:** each repo explores one approach
- [Strict PDF QA](https://github.com/dojedaro/strict-pdf-question-answering): document-only answers that resist hallucination
- [10-K retrieval evaluation](https://github.com/dojedaro/coca-cola-10k-retrieval-evaluation): SEC filings, reranking, Precision@K
- [Policy QA evaluation](https://github.com/dojedaro/openai-rag-policy-qa-evaluation): LlamaParse + ChromaDB with model comparisons
- [PDF RAG + ReAct agent](https://github.com/dojedaro/pdf-rag-react-agent-langchain): FAISS retrieval plus tool reasoning
- [Claude PDF chatbot](https://github.com/dojedaro/Claude-pdf-rag-chatbot): grounded answers with Hugging Face embeddings

**Agents and multimodal**
- [CrewAI multi-agent workflows](https://github.com/dojedaro/crewai-claude-multiagent-workflows)
- [Multimodal Claude chatbot](https://github.com/dojedaro/multimodal-claude-chatbot)
- [Video → text pipeline (ASR + OCR)](https://github.com/dojedaro/multimodal-media-to-text-pipeline)

**ML and deep learning**
- [Audio event classification (CNNs)](https://github.com/dojedaro/Audio-Event-Classification-Deep-Learning) · [Transfer learning for audio anomaly detection](https://github.com/dojedaro/transfer-learning-audio-anomaly-detection)
- [NYC taxi trip duration (LightGBM)](https://github.com/dojedaro/nyc-taxi-trip-duration-analysis-and-prediction) · [CarbonMindful: AI training emissions](https://github.com/dojedaro/carbonmindful)
</details>

---

## 🧰 Toolbox

**LLMs and agents:** Claude, OpenAI and Gemini APIs · tool use and agent loops · LangGraph · CrewAI · LangChain · LlamaIndex · MCP
**Retrieval:** ChromaDB · FAISS · BM25 · reranking · retrieval evaluation (Precision@K)
**ML:** PyTorch · Hugging Face Transformers/PEFT · QLoRA · scikit-learn · LightGBM · Whisper
**Engineering:** Python · TypeScript · FastAPI · Express · SQL · Docker · GitHub Actions · pytest/Vitest

---

## 📫 Contact

📧 d.ojedaro@gmail.com · 📍 South Korea
