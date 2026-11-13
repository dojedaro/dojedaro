# Hi, I'm Daniel 👋

**AI Engineer** based in South Korea 🇰🇷, building LLM systems that are grounded, evaluated, and safe to put in front of users: RAG, tool-using agents, and the engineering around them (APIs, tests, CI, deployment). My current focus is AI for digital identity and regulatory compliance.

I care about the parts that decide whether an AI system can be trusted: retrieval that cites its sources, agents whose tools do real work, and evaluations that measure what matters. Every number in my READMEs comes from saved outputs, and where a result is weaker than it looks, the README says so.

---

## 🔭 Featured projects

### [factcheck-agents](https://github.com/dojedaro/factcheck-agents): a multi-agent research team, measured against a single agent · [replay real runs](https://dojedaro.github.io/factcheck-agents/)
A planner, parallel researchers with web search, a critic and a writer, orchestrated in plain `asyncio` on the Claude API with no agent framework. Code, not a model, checks that every cited URL came from a real search and every citation points to evidence that passed the critic. Budgets, failure isolation, traces, and an eval with a position-swapped judge: the single agent won 3-2, and the README explains why.
`Python` `asyncio` `Claude API` `Multi-agent` `Evaluation`

### [F1 Graph RAG vs. vector RAG](https://github.com/dojedaro/f1-graphrag): when does a knowledge graph beat vector search? · [explore every run](https://dojedaro.github.io/f1-graphrag/)
A knowledge graph of 26 Formula 1 seasons with typed tools for a Claude agent, against vector RAG on the same model. On 160 structured questions with answers computed from the data, vector search gets 97% of single-fact questions but **8% of counting questions**; the graph agent gets all 160, including 40 held-out questions written after the tools existed.
`Knowledge graphs` `Tool use` `RAG` `Evaluation` `Claude API`

### [Trust Me, It Works](https://github.com/dojedaro/trust-me-it-works): can an AI tell when its own code is wrong?
Six checking strategies on 12 original "trap" coding tasks, scored by hidden tests the models never see. Self-checking approved wrong code **1 time in 4**; a different checker cut that to about **1 in 20**. The coding model never disputed a failing test, even the wrong ones. 144 runs for $3.82, with 95% confidence intervals.
`Evaluation` `Code generation` `Claude API` `Sandboxing` `pytest`

### [Aegis](https://github.com/dojedaro/aegis): AI compliance operations platform · [live demo](https://aegis-web-xi.vercel.app/)
A Claude agent that reviews systems against GDPR, eIDAS 2.0, AML/KYC and the EU AI Act. Its tools do the parts that must be exact: BM25 retrieval over real regulation articles, deterministic PII scanning, and findings that must cite an article that exists. RBAC audit trail, explainable KYC risk scoring, and 92 tests.
`TypeScript` `Claude tool use` `RAG` `JWT/RBAC` `Vitest` `Playwright`

### Also built
- [Say What?](https://github.com/dojedaro/say-what): video Q&A in English, Spanish and Korean with timestamped citations; refuses when retrieval finds nothing. FastAPI, ChromaDB, 4 LLM providers, 61 tests.
- [MCP-TRADI-WIN](https://github.com/dojedaro/tradiwin-explainable-trading-agents) (Master's thesis): multi-agent crypto forecasting under the Model Context Protocol, where LLMs explain decisions but never make them.
- [QLoRA fine-tuning](https://github.com/dojedaro/qlora-bert-sentiment-classification): 91.6% test accuracy on 10,000 IMDB reviews while training 0.44% of BERT's weights, under 1 GB of GPU memory.
- [LangGraph competitive-intelligence agent](https://github.com/dojedaro/langgraph-competitive-intelligence-agent): a Claude agent that maps nearby competitors with the Google Places API and writes a business report.

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
