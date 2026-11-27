# Daniel Ojeda

**AI engineer in Seoul. I build LLM agents and RAG systems, and I measure whether they work.**

**Now:** AI Engineer / AI Enabler Lead at Hopae, where I built and run several Claude-based production systems, including a finance agent whose decisions are checked by a second Claude model, with human approval for new vendors; a company-knowledge RAG assistant over Slack, Notion, HubSpot, Drive and GitHub; and a competitor-monitoring agent. **Before:** 8+ years of applied ML and analytics (Scotiabank, Iris Pricing Solutions). MBA and Master of Management Analytics (Queen's), M.Eng. in AI (Woosong). English, Spanish, French; conversational Korean.

[Portfolio](https://daniel-ojeda.vercel.app) · [한국어](https://daniel-ojeda.vercel.app/ko) · [LinkedIn](https://www.linkedin.com/in/danielojedar) · d.ojedaro@gmail.com

**Measured, from saved outputs:**
- Rolling upgrades and a rollback of an LLM guardrail gateway on Kubernetes: **0 of 2,994** requests failed; with its upstream deliberately killed, the same probe saw 119 of 691 fail ([llm-guardrail-k8s](https://github.com/dojedaro/llm-guardrail-k8s))
- Same model, three retrieval designs, 160 questions: one-shot vector RAG **55%**, a vector-search agent **94%**, knowledge-graph tools **100%** ([F1](https://github.com/dojedaro/f1-graphrag))
- A model checking its own code approved wrong code in **4 of 17** cases; a separate, larger checker in **1 of 20** (small samples, intervals overlap) ([Trust Me](https://github.com/dojedaro/trust-me-it-works))
- A fine-tuned 1.5B LLM scored **83%** and TF-IDF **85%**, reported as a tie ([QLoRA triage](https://github.com/dojedaro/qlora-maintenance-triage))
- On 5 questions, a team of agents lost **3-2** to a single agent that cost 30% less ([factcheck-agents](https://github.com/dojedaro/factcheck-agents))

---

## How I build agents

When an agent fails, the prompt is rarely the problem. I design and measure the layers around the model, and my projects test them with the model held fixed:

| Layer | What I design | What I measured |
|---|---|---|
| **Context**: what the model sees on each call | Typed tools instead of raw text chunks; each agent sees only its own tools | Same model, different tools: one-shot retrieval **55%**, a search loop **94%**, knowledge-graph tools **100%** ([F1](https://github.com/dojedaro/f1-graphrag)) |
| **Loop**: trigger, goal, verification, memory | Verification that runs tests rather than giving opinions; an iteration cap and a stop when nothing changes | A separate checker (a larger model scoring the code, or tests that actually run) raised correctness from **58%** to **92–96%**; self-checking approved wrong code in **4 of 17** cases ([Trust Me, It Works](https://github.com/dojedaro/trust-me-it-works)) |
| **Harness**: the code that runs it reliably | Guarantees enforced in code: sandboxes, budgets, retries, resumable runs, traces | Code rejects any citation that didn't come from a real search ([factcheck-agents](https://github.com/dojedaro/factcheck-agents)); findings must cite a regulation article that exists ([Aegis](https://github.com/dojedaro/aegis)) |

In production at Hopae, a finance agent combines all three: it runs hourly, a verifier on a different Claude model checks every decision, new vendors need human approval, and corrections are saved as rules for future runs.

---

## Featured projects

The projects below are my public work, built with Claude Code as a pair programmer. I set the questions, the experimental design and the acceptance criteria, and every number comes from saved outputs you can open. My day-job code is private.

### [LLM guardrail on Kubernetes](https://github.com/dojedaro/llm-guardrail-k8s): deploying an AI-security gateway into a cluster, end to end
A gateway in front of an LLM API that redacts PII and screens prompt injection, packaged as a Helm chart and taken through a full deployment on a 3-node kind cluster (Calico) and on k3s on Ubuntu: environment assessment, a simulated air-gapped install from a checksummed bundle, default-deny NetworkPolicies proven by a probe that must connect first and then be blocked, rolling upgrades and rollback with **0 of 2,994** requests failed, and eight drills with real diagnoses, including a Helm 4 field-ownership conflict written up as a customer-style incident report. The guardrails' weak spots are published: on 45 prompts written by an independent reviewer, the first phrase rules blocked 21 of 25 safe prompts and missed 15 of 20 attacks; after narrowing them, 3 of 25 and 6 of 20, measured on the same prompts and stated as such.
`Kubernetes` `Helm` `k3s` `NetworkPolicy` `Air-gapped install` `AI security`

### [QLoRA maintenance triage](https://github.com/dojedaro/qlora-maintenance-triage): is a fine-tuned LLM worth its GPU on real fault reports?
Qwen2.5-1.5B fine-tuned with QLoRA to predict which component a metro train needs repaired, from 3,700 real maintenance fault reports with the repair text cut out so the model cannot read the answer. Fine-tuning lifts accuracy from **52%** to **83%** and cuts made-up answers from 12.7% to 0.1%; a TF-IDF baseline scores **85%**, a statistical tie (McNemar p = 0.15), and wins on rare components. Bootstrap intervals, leakage and near-duplicate audits, and an error analysis of why: one symptom often has several valid repairs.
`QLoRA` `PEFT` `Qwen2.5` `Evaluation` `Industrial data`

### [VLM defect inspection](https://github.com/dojedaro/vlm-defect-inspection): how many defects are caught at 10% false alarms?
On MVTec AD, a PatchCore-style detector that learns only from good parts reaches AUROC **0.974** and catches 98% / 83% / 100% of defects at 10% false alarms (metal nut / screw / transistor). Qwen2.5-VL-3B zero-shot reaches **0.751** and never says "defective" at its default threshold. Fine-tuned ResNet-18 in between, 3 seeds, same held-out images.
`Computer vision` `Anomaly detection` `Vision-language models` `PyTorch` `Evaluation`

### [factcheck-agents](https://github.com/dojedaro/factcheck-agents): a multi-agent research team, measured against a single agent · [replay real runs](https://dojedaro.github.io/factcheck-agents/)
A planner, parallel researchers with web search, a critic and a writer, orchestrated in plain `asyncio` on the Claude API with no agent framework. Code, not a model, checks that every cited URL came from a real search and every citation points to evidence that passed the critic. Budgets, failure isolation, traces, and an eval with a position-swapped judge: the single agent won 3-2, and the README explains why.
`Python` `asyncio` `Claude API` `Multi-agent` `Evaluation`

### [F1 Graph RAG vs. vector RAG](https://github.com/dojedaro/f1-graphrag): when does a knowledge graph beat vector search? · [explore every run](https://dojedaro.github.io/f1-graphrag/)
A knowledge graph of 26 Formula 1 seasons with typed tools for a Claude agent, against vector RAG on the same model. On 160 structured questions with answers computed from the data, one-shot vector search scores **55%** (8% on counting); a vector agent that searches in a loop reaches **94%**; the graph agent gets **all 160**, including 40 held-out questions written after the tools existed, at a quarter of the vector agent's cost.
`Knowledge graphs` `Tool use` `RAG` `Evaluation` `Claude API`

### [Trust Me, It Works](https://github.com/dojedaro/trust-me-it-works): can an AI tell when its own code is wrong?
Six checking strategies on 12 original "trap" coding tasks, scored by hidden tests the models never see. Self-checking approved wrong code in **4 of 17** cases, a separate, larger checker model in **1 of 20** (small samples, stated with intervals). The coding model never disputed a failing test, even the wrong ones. 144 runs for about $4, with 95% confidence intervals.
`Evaluation` `Code generation` `Claude API` `Sandboxing` `pytest`

### [Aegis](https://github.com/dojedaro/aegis): AI compliance operations platform · [live demo](https://aegis-web-xi.vercel.app/)
A Claude agent that reviews systems against GDPR, eIDAS 2.0, AML/KYC and the EU AI Act. Its tools do the parts that must be exact: BM25 retrieval over a curated library of 26 article summaries linked to EUR-Lex, deterministic PII scanning, and findings that must cite an article in that library. On 11 author-written cases (one run) it found all 14 planted violations, with no findings on the 2 clean controls. RBAC audit trail, explainable KYC risk scoring, and 80 tests in CI.
`TypeScript` `Claude tool use` `RAG` `JWT/RBAC` `Vitest` `Playwright`

### Also built
- [Say What?](https://github.com/dojedaro/say-what): video Q&A in English, Spanish and Korean with timestamped citations; refuses when retrieval finds nothing. FastAPI, ChromaDB, 4 LLM providers, 62 tests.
- [MCP-TRADI-WIN](https://github.com/dojedaro/tradiwin-explainable-trading-agents) (Master's thesis): multi-agent crypto forecasting under the Model Context Protocol, where LLMs explain decisions but never make them.
- [QLoRA vs. LoRA vs. full fine-tuning](https://github.com/dojedaro/qlora-bert-sentiment-classification): all three measured on one GPU. Training only adapters cuts peak memory from 2.32 GB to 1.23 GB at a 0.7-point accuracy cost; the 4-bit part of QLoRA adds no saving on BERT, only a 2x slower prediction.
- [CarbonMindful](https://github.com/dojedaro/carbonmindful): carbon footprint of AI training runs across regional scenarios; the paper is accepted at the International Journal of Environment and Waste Management.
- [LangGraph competitive-intelligence agent](https://github.com/dojedaro/langgraph-competitive-intelligence-agent): a Claude agent that maps nearby competitors with the Google Places API and writes a business report.

### What measuring taught me
- **A model's own "looks good" is not a quality gate.** Self-review approved wrong code in 4 of 17 cases; a separate, larger model did in 1 of 20 ([trust-me-it-works](https://github.com/dojedaro/trust-me-it-works)).
- **A team of agents lost to one agent** (with the team's follow-up round off), on coverage rather than accuracy ([factcheck-agents](https://github.com/dojedaro/factcheck-agents#does-the-team-beat-one-agent)).
- **97% accuracy can miss most of what matters:** a bankruptcy model that caught 9 of 44 bankruptcies until rebalanced ([bankruptcy prediction](https://github.com/dojedaro/bankruptcy-prediction-imbalanced-classification)).
- **A confident agent can be wrong in a way its reasoning hides:** cos(60°) computed in radians ([ReAct agent](https://github.com/dojedaro/pdf-rag-react-agent-langchain)).
- **Metrics need checking too:** word-overlap scoring ranked a small model above GPT-3.5 ([policy QA](https://github.com/dojedaro/openai-rag-policy-qa-evaluation)), and a cleanly explained model was barely better than always guessing the most common class ([explainable AI](https://github.com/dojedaro/explainable-ai-shap-lime)).

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
- [NYC taxi trip duration (LightGBM)](https://github.com/dojedaro/nyc-taxi-trip-duration-analysis-and-prediction)
</details>

---

## Toolbox

**LLMs and agents:** Claude, OpenAI and Gemini APIs · context, loop and harness engineering · tool use · LangGraph · CrewAI · AutoGen · LangChain · LlamaIndex · MCP
**Retrieval and evaluation:** knowledge graphs (NetworkX) · ChromaDB · FAISS · BM25 · reranking · Precision@K · position-swapped LLM judges · confidence intervals
**ML:** PyTorch · TensorFlow/Keras · Hugging Face Transformers/PEFT/tokenizers · QLoRA · scikit-learn · XGBoost · LightGBM · SHAP/LIME · Whisper
**Engineering:** Python · TypeScript · FastAPI · Express · SQL · Docker · GitHub Actions · pytest/Vitest

---

## Contact

d.ojedaro@gmail.com · Seoul, South Korea · [LinkedIn](https://www.linkedin.com/in/danielojedar) · [Portfolio](https://daniel-ojeda.vercel.app)
