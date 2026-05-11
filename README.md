# Papers
Papers written for Istanbul Technical University Computer Engineering Courses
# "I'm Afraid I Can't Do That": Multi-layered Defense Architecture for Prompt Safety

This research paper was developed for the **BLG 459E - Computer Security** course at **Istanbul Technical University (İTÜ)**, Computer Engineering Department.

## 👥 Authors
* Bera Kerem Pişkin
* Kaleab Abayneh Gizawa
* **Melih Demir**
* Merve Hatun Özcan
* Onat Budak

## 📝 Abstract
As Large Language Models (LLMs) become integrated into agentic systems, they face critical vulnerabilities, most notably **Prompt Injection**. This paper proposes a low-cost, multi-layered defense pipeline designed to neutralize malicious instructions before they reach the AI agent. Our solution reduces the Attack Success Rate (ASR) from **92%** in unprotected systems to **0.36%** in our full implementation.

## 🏗️ System Architecture
The defense mechanism is a pipeline consisting of five specialized modules, formalised using **Linear Temporal Logic (LTL)** to ensure strict execution order and integrity.


1.  **Canonicalization Module:** Normalizes input (Unicode, Base64 decoding, whitespace) to prevent obfuscation attacks.
2.  **Regex Module:** A deterministic filter that identifies known attack signatures (PII leaks, jailbreak patterns) with low computational cost.
3.  **Semantic Classifier:** A machine learning-based module using **MiniLM embeddings** to analyze the contextual intent of the prompt.
4.  **Policy Module:** The central decision engine that evaluates risk scores against predefined security thresholds (e.g., "Ironclad" threshold of 0.50).
5.  **Paraphraser LLM:** A final generative layer (Llama-3.3-70b) that rewrites approved prompts to strip any remaining adversarial triggers while preserving utility.

## 📊 Key Results
We tested the architecture against a dataset of **840 prompts**, including Direct Tool Abuse, Jailbreaks, and Social Engineering scenarios.

| Defense Stage | Attack Success Rate (ASR) |
| :--- | :--- |
| **Baseline (No Defense)** | 92% |
| **Filters Only** | 0.83% |
| **Full Solution (Filters + Paraphraser)** | **0.36%** |

## 🛠️ Tech Stack
* **Language:** Python
* **Libraries:** PyTorch (Model Optimization), Transformers (MiniLM), Unicodedata
* **LLM Engine:** Llama-3.3-70b-versatile (for Paraphrasing)
* **Formal Verification:** Linear Temporal Logic (LTL)

## 📂 Citation & Full Text
The complete research paper is available in the `/Paper` directory of this repository.
