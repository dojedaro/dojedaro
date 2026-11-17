# Daniel Ojeda

**Applied AI engineer with a business background, based in Seoul.** I hold an MBA and a Master of Management Analytics (Smith School of Business, Queen's University) and a master's in AI, and I have 8+ years across banking, pricing consulting and AI engineering in Canada, Mexico and South Korea.

I start from the business question: what decision the system informs, what a wrong answer costs, and what it costs to run. Then I build the LLM system (RAG, agents, tool use) and measure whether it works before anyone relies on it.

- **Now:** AI Engineer / AI Enabler Lead at Hopae (digital identity), where I design and deploy production LLM applications end to end.
- **Before:** Senior Manager, AI/ML Engineering and Business Intelligence at Scotiabank; Analytics Consultant at Iris Pricing Solutions.
- **Languages:** English, Spanish, conversational Korean.

[Portfolio site](https://daniel-ojeda.vercel.app) · [LinkedIn](https://www.linkedin.com/in/danielojedar) · d.ojedaro@gmail.com

> The projects below are my public work, built with Claude Code as a pair programmer. I set the questions, the experimental design and the acceptance criteria, and every number comes from saved outputs you can open. My day-job code is private.

---

## What measuring taught me

- **Don't pay for a multi-agent system until it beats one agent per dollar on your own questions.** In my first 5-question test the single agent won 3-2 at 30% lower cost, with the team's follow-up round off ([factcheck-agents](https://github.com/dojedaro/factcheck-agents#does-the-team-beat-one-agent)).
- **A model's own "looks good" is not a quality gate.** Self-review approved wrong code in 4 of 17 cases; a stronger second model did in 1 of 20 ([trust-me-it-works](https://github.com/dojedaro/trust-me-it-works)).
- **For counts and joins over records you already hold, give the model query tools, not a search index.** 100% against 94% on 160 questions, at about a quarter of the cost ([f1-graphrag](https://github.com/dojedaro/f1-graphrag)).
- **97% accuracy can miss most of what matters.** A bankruptcy model caught 9 of 44 bankruptcies until the classes were rebalanced ([bankruptcy prediction](https://github.com/dojedaro/bankruptcy-prediction-imbalanced-classification)).
- **Metrics need checking too.** Word-overlap scoring ranked a small model above GPT-3.5 ([policy QA](https://github.com/dojedaro/openai-rag-policy-qa-evaluation)), and a cleanly explained model was barely better than always guessing the most common class ([explainable AI](https://github.com/dojedaro/explainable-ai-shap-lime)).

## Featured projects

### [F1 Graph RAG vs. vector RAG](https://github.com/dojedaro/f1-graphrag) · [explore every run](https://dojedaro.github.io/f1-graphrag/)
Which retrieval design answers data questions correctly? On 160 Formula 1 questions with answers computed from the data, plain vector search scored **55%**, a vector-search agent **94%**, and an agent with typed graph tools **100%**, at a quarter of the vector agent's cost. 40 of the questions were written after the tools existed.

### [factcheck-agents](https://github.com/dojedaro/factcheck-agents) · [replay real runs](https://dojedaro.github.io/factcheck-agents/)
A team of AI agents that researches a question and checks its own citations in code: every cited URL must come from a real search. Tested against a single agent on cost and quality; on the first 5 questions the single agent won 3-2, and the README says why.

### [Trust Me, It Works](https://github.com/dojedaro/trust-me-it-works)
Can an AI tell when its own code is wrong? Six ways of checking AI-written code, scored by hidden tests the models never see, on the 12 novel tasks of a 24-task set. 144 runs for about $4, reported with 95% confidence intervals.

### [Aegis](https://github.com/dojedaro/aegis) · [live demo](https://aegis-web-xi.vercel.app/)
An AI compliance reviewer for GDPR, eIDAS 2.0, AML/KYC and the EU AI Act that cannot invent a citation: code rejects any finding whose article is not in its regulation library. On an 11-case smoke test with author-written cases it found all 14 planted violations with no false alarms; real documents are the next test.

[![Aegis compliance dashboard](https://raw.githubusercontent.com/dojedaro/aegis/main/docs/screenshots/overview.png)](https://aegis-web-xi.vercel.app/)

### Also built
- [Say What?](https://github.com/dojedaro/say-what): ask questions about any video in English, Spanish or Korean and get answers with timestamps; it refuses when the transcript has no answer.
- [CarbonMindful](https://github.com/dojedaro/carbonmindful): carbon footprint of AI training runs across regional scenarios; the paper is accepted at the International Journal of Environment and Waste Management.
- [MCP-TRADI-WIN](https://github.com/dojedaro/tradiwin-explainable-trading-agents) (master's thesis): multi-agent crypto forecasting where LLMs explain decisions but never make them.
- [QLoRA fine-tuning](https://github.com/dojedaro/qlora-bert-sentiment-classification): 91.6% test accuracy on 10,000 IMDB reviews while training 0.44% of BERT's weights.

<details>
<summary><b>More work</b>: RAG series, agents, multimodal, classical ML</summary>

**RAG techniques series:** each repo explores one approach
- [Strict PDF QA](https://github.com/dojedaro/strict-pdf-question-answering): document-only answers that resist hallucination
- [10-K retrieval evaluation](https://github.com/dojedaro/coca-cola-10k-retrieval-evaluation): SEC filings, reranking, Precision@K
- [Policy QA evaluation](https://github.com/dojedaro/openai-rag-policy-qa-evaluation): LlamaParse + ChromaDB with model comparisons
- [PDF RAG + ReAct agent](https://github.com/dojedaro/pdf-rag-react-agent-langchain): FAISS retrieval plus tool reasoning, including an agent that computed cos(60°) in radians
- [Research-paper RAG](https://github.com/dojedaro/research-paper-rag-qa-system): hybrid BM25 + semantic retrieval
- [Claude PDF chatbot](https://github.com/dojedaro/claude-pdf-rag-chatbot): grounded answers with sources · [live demo](https://claude-pdf-rag-chatbot.streamlit.app/)

**Agents and multimodal**
- [LangGraph competitive-intelligence agent](https://github.com/dojedaro/langgraph-competitive-intelligence-agent) · [CrewAI multi-agent workflows](https://github.com/dojedaro/crewai-claude-multiagent-workflows) · [AutoGen agents on Claude for EDA](https://github.com/dojedaro/autogen-claude-eda-agents)
- [Prompt engineering: zero-, one- and few-shot evaluation](https://github.com/dojedaro/prompt-engineering-few-shot-learning)
- [Multimodal Claude chatbot](https://github.com/dojedaro/multimodal-claude-chatbot) · [live demo](https://multimodal-claude-chatbot.streamlit.app/)
- [Video → text pipeline (ASR + OCR)](https://github.com/dojedaro/multimodal-media-to-text-pipeline) · [Text-to-video with diffusion models](https://github.com/dojedaro/diffusers-text-to-video)

**ML and deep learning**
- [BPE tokenizer from scratch](https://github.com/dojedaro/bpe-tokenizer-from-scratch) · [Explainable AI with SHAP and LIME](https://github.com/dojedaro/explainable-ai-shap-lime) · [Bankruptcy prediction on imbalanced data](https://github.com/dojedaro/bankruptcy-prediction-imbalanced-classification)
- [Audio event classification (CNNs)](https://github.com/dojedaro/audio-event-classification) · [Transfer learning for audio anomaly detection](https://github.com/dojedaro/transfer-learning-audio-anomaly-detection)
- [NYC taxi trip duration (LightGBM)](https://github.com/dojedaro/nyc-taxi-trip-duration-analysis-and-prediction)
</details>

---

## Toolbox

**LLMs and agents:** Claude, OpenAI and Gemini APIs · tool use and agent loops · MCP · LangGraph · LangChain
**Retrieval and evaluation:** knowledge graphs · vector stores (ChromaDB, FAISS) · BM25 · LLM judges · confidence intervals
**ML:** PyTorch · Hugging Face Transformers/PEFT · scikit-learn · XGBoost/LightGBM · SHAP/LIME
**Engineering:** Python · TypeScript · FastAPI · SQL · Docker · GitHub Actions

---

[Portfolio site](https://daniel-ojeda.vercel.app) · [LinkedIn](https://www.linkedin.com/in/danielojedar) · d.ojedaro@gmail.com · Seoul, South Korea
