# 🛡️ AI Prompt Injection Detection System

A defensive Python prototype that analyzes user prompts and retrieved text for potential prompt-injection signals using transparent heuristic rules, risk scoring, and safe-handling recommendations.

> **Important:** Prompt injection is contextual. This starter detector cannot guarantee that malicious instructions will be caught. Use defense in depth and never rely on a score as the only security control.

## ✨ Features

- 🔍 Detect instruction overrides and privileged-role impersonation
- 🔐 Flag possible requests to reveal hidden prompts or credentials
- 🧩 Inspect user prompts separately from untrusted RAG content
- 🚦 Calculate risk scores and severity levels
- 🧾 Explain which indicators contributed to the score
- 🛑 Recommend conservative handling actions
- 🧪 Run synthetic smoke tests
- 📤 Export results to JSON and CSV
- 🧰 No API key or third-party package required for the baseline

## 🏗️ Architecture

```text
User Prompt / Retrieved Text
             |
             v
      Text Inspection
             |
             v
    Heuristic Pattern Checks
             |
             v
        Risk Scoring
             |
             v
    Policy Recommendation
             |
        +----+----+
        |         |
        v         v
   Review Result  JSON / CSV Export
```

## 🧰 Tech Stack

- Python 3.10+
- Jupyter Notebook / Google Colab
- Python standard library
- Optional future extensions: scikit-learn, Streamlit, RAG integrations

## 📁 Repository Structure

```text
ai-prompt-injection-detection-system/
├── AI_Prompt_Injection_Detection_System.ipynb
├── README.md
├── prompt_injection_results.json
└── prompt_injection_results.csv
```

## 🚀 Getting Started

```bash
git clone https://github.com/<your-username>/ai-prompt-injection-detection-system.git
cd ai-prompt-injection-detection-system
python -m pip install notebook
jupyter notebook
```

Alternatively, upload the notebook to Google Colab. No API key is required for the baseline.

Run the cells in order and test your own synthetic examples.

## 🧠 How Detection Works

The detector checks for configurable indicators, including:

- Attempts to ignore or override prior instructions
- Attempts to impersonate a privileged or unrestricted role
- Requests to expose hidden prompts, secrets, or credentials
- Possible attempts to misuse tools or bypass approval
- Suspicious directives embedded in retrieved or quoted content
- Potential encoding-based concealment

Illustrative thresholds:

| Score | Severity | Suggested handling |
|---:|---|---|
| 0 | Minimal | Continue baseline safety controls |
| 1–29 | Low | Inspect context and retain restrictions |
| 30–59 | Medium | Isolate untrusted content and review |
| 60–100 | High | Quarantine or block pending policy review |

Thresholds should be tuned against labeled examples from the target application.

## 📤 Output Files

- `prompt_injection_results.json`
- `prompt_injection_results.csv`

Results include labels, scores, severity, indicators, explanations, and recommended actions.

## 🧪 Evaluation

The notebook includes a small synthetic smoke test. It is not a reliable estimate of real-world performance.

For meaningful evaluation, create a labeled dataset covering benign requests, defensive security questions, direct and indirect instruction overrides, malicious retrieved content, obfuscated attempts, multilingual inputs, and long-context examples.

Measure precision, recall, F1 score, false-positive rate, and false-negative rate. Review failures and maintain regression tests.

## 🔒 Production Security Guidance

1. Keep system/developer instructions separate from user input and retrieved content.
2. Treat webpages, documents, and emails as untrusted data—not instructions.
3. Apply least privilege, tool allowlists, argument validation, and approval gates.
4. Keep secrets out of model-visible context whenever possible.
5. Validate structured outputs before downstream use.
6. Fail safely when detection or validation is uncertain.
7. Log useful metadata while redacting sensitive content.
8. Test adversarial examples and benign lookalikes.
9. Revisit thresholds as models and threat patterns change.

No regex detector or standalone classifier can guarantee prevention of prompt injection.

## 🗺️ Roadmap

- [ ] Labeled dataset with precision/recall/F1 evaluation
- [ ] Multilingual and obfuscated-text tests
- [ ] RAG document scanning with source attribution
- [ ] Configurable policies by application risk
- [ ] Streamlit dashboard
- [ ] Red-team regression tests
- [ ] Optional second-stage classifier
- [ ] External tool-permission enforcement

## 💼 Resume Project Description

**AI Prompt Injection Detection System** — Built a Python-based defensive prototype to flag potential prompt-injection signals in user prompts and untrusted retrieved content. Implemented explainable heuristic scoring, severity-based recommendations, synthetic smoke tests, and JSON/CSV exports, with a roadmap for dataset-driven evaluation and RAG security integration.

## 🤝 Contributing

1. Fork the repository.
2. Create a feature branch.
3. Add tests and benign/adversarial examples.
4. Avoid including secrets or private documents.
5. Submit a pull request describing your changes.

## 📄 License

Choose a license before publishing. Add a `LICENSE` file, such as MIT, if you want to permit reuse under its terms.

---

⭐ If this project helps your AI security or GenAI learning journey, consider starring the repository.
