# Hi, I'm Daniel 👋

**AI Engineer** based in South Korea 🇰🇷, building LLM systems that are grounded, evaluated, and safe to put in front of users: RAG, tool-using agents, and the engineering around them (APIs, tests, CI, deployment).

I care about the unglamorous parts that decide whether an AI system can be trusted: retrieval that cites its sources, agents whose tools do real work, and responses that say when they *don't* know. Every number in my READMEs comes from saved outputs, and where a result is weaker than it looks, the README says so.

---

## 🔭 Featured projects

### [factcheck-agents](https://github.com/dojedaro/factcheck-agents): a multi-agent research team, measured against a single agent · [replay real runs](https://dojedaro.github.io/factcheck-agents/)
A planner, parallel researchers with web search, a critic and a writer, orchestrated in plain `asyncio` on the Claude API with no agent framework. Code, not a model, checks that every cited URL came from a real search and that every citation points to evidence that passed fact-checking. It has budgets with a reserve, failure isolation, nested traces, and an eval with a position-swapped LLM judge. The first eval went 3-2 to the single agent; the README explains why and what to try next.
`Python` `asyncio` `Claude API` `Multi-agent` `Structured outputs` `Evaluation`

### [F1 Graph RAG vs. vector RAG](https://github.com/dojedaro/f1-graphrag): when does a knowledge graph beat vector search? · [explore every run](https://dojedaro.github.io/f1-graphrag/)
A knowledge graph of 26 Formula 1 seasons with typed tools for a Claude agent, against vector RAG on the same model. 160 questions with answers computed from the data, scored by hop count: vector search gets 97% of single-fact questions but **8% of counting questions**; the graph agent gets all 160, including 40 held-out questions written after the tools existed (6 tool calls each, composing general tools). The whole evaluation cost $0.38.
`Knowledge graphs` `Tool use` `RAG` `Evaluation` `NetworkX` `Claude API`

### [Trust Me, It Works](https://github.com/dojedaro/trust-me-it-works): can an AI tell when its own code is wrong?
Six checking strategies (self-check, a second model scoring, a second model writing tests that run, disputes, hidden-test oracle) on 24 original "trap" coding tasks, scored by hidden tests the models never see. Self-checking approved wrong code **1 time in 4**; a different checker cut that to about **1 in 20**. The maker never disputed a single failing test, even the wrong ones. 144 runs for $3.82, with 95% confidence intervals.
`Evaluation` `Code generation` `Claude API` `Sandboxing` `pytest`

### [Aegis](https://github.com/dojedaro/aegis): AI compliance operations platform · [live demo](https://aegis-web-xi.vercel.app/)
Compliance review for GDPR, eIDAS 2.0, AML and the EU AI Act. A Claude agent uses tools that do real work: regulation retrieval (BM25), deterministic PII scanning, and finding recording that rejects citations to articles that don't exist. Explainable rule-based KYC risk scoring, an RBAC-protected audit trail, and 75 tests.
`TypeScript` `Express` `Claude tool use` `RAG` `JWT/RBAC` `Vitest`

### [Say What?](https://github.com/dojedaro/say-what): multilingual video Q&A with grounded RAG
Transcribes, translates and indexes YouTube/TikTok/Instagram videos, then answers questions in English, Spanish or Korean with timestamped citations. It refuses to answer when retrieval finds nothing relevant. One interface for OpenAI, Claude, Gemini and Azure.
`Python` `FastAPI` `ChromaDB` `Whisper` `pytest` `Docker`

### [MCP-TRADI-WIN](https://github.com/dojedaro/tradiwin-explainable-trading-agents): explainable multi-agent trading (Master's thesis)
A multi-agent crypto forecasting framework combining time-series models and sentiment analysis under the Model Context Protocol. LLMs are used strictly for *explanation*, never for the trading decision itself.
`Multi-agent` `MCP` `Time series` `Explainable AI`

### [Research Paper RAG](https://github.com/dojedaro/research-paper-rag-qa-system): Q&A over academic papers
Hybrid BM25 + semantic retrieval over five landmark AI papers, with strict source grounding and conversation memory, served via Streamlit.
`RAG` `Evaluation` `Streamlit`

### [QLoRA fine-tuning](https://github.com/dojedaro/qlora-bert-sentiment-classification): parameter-efficient BERT
4-bit NF4 quantization with LoRA adapters: **91.6% test accuracy (AUC 0.971) on 10,000 IMDB reviews while training 0.44% of the weights**, peaking under 1 GB of GPU memory.
`PEFT` `QLoRA` `bitsandbytes` `Hugging Face`

### [LangGraph competitive-intelligence agent](https://github.com/dojedaro/langgraph-competitive-intelligence-agent)
A Claude agent in a LangGraph loop that finds nearby competitors with the Google Places API, estimates busy hours, and writes a business report. Its README documents a location bug I found and fixed.
`LangGraph` `Agents` `Tool integration`

### What measuring taught me
- **A team of agents lost to one agent**, on coverage rather than accuracy ([factcheck-agents](https://github.com/dojedaro/factcheck-agents#does-the-team-beat-one-agent)).
- **97% accuracy can miss most of what matters:** a bankruptcy model that caught 9 of 44 bankruptcies until rebalanced ([bankruptcy prediction](https://github.com/dojedaro/bankruptcy-prediction-imbalanced-classification)).
- **A confident agent can be wrong in a way its reasoning hides:** cos(60°) computed in radians ([ReAct agent](https://github.com/dojedaro/pdf-rag-react-agent-langchain)).
- **Metrics need checking too:** word-overlap scoring ranked a small model above GPT-3.5 ([policy QA](https://github.com/dojedaro/openai-rag-policy-qa-evaluation)), and a perfectly explained model was no better than its baseline ([explainable AI](https://github.com/dojedaro/explainable-ai-shap-lime)).

<details>
<summary><b>More work</b>: RAG series, multimodal, audio ML, classical ML</summary>

**RAG techniques series:** each repo explores one approach
- [Strict PDF QA](https://github.com/dojedaro/strict-pdf-question-answering): document-only answers that resist hallucination
- [10-K retrieval evaluation](https://github.com/dojedaro/coca-cola-10k-retrieval-evaluation): SEC filings, reranking, Precision@K
- [Policy QA evaluation](https://github.com/dojedaro/openai-rag-policy-qa-evaluation): LlamaParse + ChromaDB with model comparisons
- [PDF RAG + ReAct agent](https://github.com/dojedaro/pdf-rag-react-agent-langchain): FAISS retrieval plus tool reasoning
- [Research-paper RAG](https://github.com/dojedaro/research-paper-rag-qa-system): hybrid BM25 + semantic retrieval
- [Claude PDF chatbot](https://github.com/dojedaro/claude-pdf-rag-chatbot): grounded answers with sources · [live demo](https://claude-pdf-rag-chatbot.streamlit.app/)

**Agents and multimodal**
- [Prompt engineering: zero-, one- and few-shot evaluation](https://github.com/dojedaro/prompt-engineering-few-shot-learning)
- [CrewAI multi-agent workflows](https://github.com/dojedaro/crewai-claude-multiagent-workflows) · [AutoGen agents on Claude for EDA](https://github.com/dojedaro/autogen-claude-eda-agents)
- [Multimodal Claude chatbot](https://github.com/dojedaro/multimodal-claude-chatbot) · [live demo](https://multimodal-claude-chatbot.streamlit.app/)
- [Video → text pipeline (ASR + OCR)](https://github.com/dojedaro/multimodal-media-to-text-pipeline)
- [Text-to-video with diffusion models](https://github.com/dojedaro/diffusers-text-to-video)

**ML and deep learning**
- [BPE tokenizer from scratch on WikiText-2](https://github.com/dojedaro/bpe-tokenizer-from-scratch) · [Explainable AI with SHAP and LIME](https://github.com/dojedaro/explainable-ai-shap-lime) · [Bankruptcy prediction on imbalanced data](https://github.com/dojedaro/bankruptcy-prediction-imbalanced-classification)
- [Audio event classification (CNNs)](https://github.com/dojedaro/audio-event-classification) · [Transfer learning for audio anomaly detection](https://github.com/dojedaro/transfer-learning-audio-anomaly-detection)
- [NYC taxi trip duration (LightGBM)](https://github.com/dojedaro/nyc-taxi-trip-duration-analysis-and-prediction) · [CarbonMindful: AI training emissions](https://github.com/dojedaro/carbonmindful)
</details>

---

## 🧰 Toolbox

**LLMs and agents:** Claude, OpenAI and Gemini APIs · tool use and agent loops · LangGraph · CrewAI · AutoGen · LangChain · LlamaIndex · MCP
**Retrieval and evaluation:** knowledge graphs (NetworkX) · ChromaDB · FAISS · BM25 · reranking · Precision@K · position-swapped LLM judges · confidence intervals
**ML:** PyTorch · TensorFlow/Keras · Hugging Face Transformers/PEFT/tokenizers · QLoRA · scikit-learn · XGBoost · LightGBM · SHAP/LIME · Whisper
**Engineering:** Python · TypeScript · FastAPI · Express · SQL · Docker · GitHub Actions · pytest/Vitest

---

## 📫 Contact

📧 d.ojedaro@gmail.com · 📍 South Korea
