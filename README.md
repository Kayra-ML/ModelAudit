<div align="center">

<img src="banner.png" alt="Model Audit Banner" width="100%"/>

<br/><br/>

[![License: MIT](https://img.shields.io/badge/License-MIT-white?style=for-the-badge&logo=opensourceinitiative&logoColor=black&labelColor=white&color=black)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active%20Research-black?style=for-the-badge&labelColor=white&color=black)](https://github.com/Kayra-ML/ModelAudit)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-black?style=for-the-badge&labelColor=white&color=black)](CONTRIBUTING.md)
[![Stars](https://img.shields.io/github/stars/Kayra-ML/ModelAudit?style=for-the-badge&labelColor=white&color=black&logo=github&logoColor=black)](https://github.com/Kayra-ML/ModelAudit/stargazers)

<br/>

> **"A model that hides its identity is a model that hides its risks."**

<br/>

# Model Audit

### LLM Identity Forensics & Transparency Verification Framework

*Cutting through the costume. Exposing the core.*

---

</div>

## 📌 What Is This?

**ModelAudit** is an open research framework for **verifying the true identity of Large Language Models (LLMs)** — regardless of what name, persona, or "costume" they are presented under.

When you access an AI assistant through an API or a product, you are often told *what* the model is supposed to be. But is it? This project provides the tools and methodology to find out.

It operates on two fronts:

| Module | Purpose |
|--------|---------|
| 🔬 **Identity Forensics** | Detect the real model through technical signals — context window, tokenizer artifacts, error patterns, latency fingerprints, behavioral biases |
| 💬 **Identity Truth Prompts** | Craft adversarial prompts that bypass persona layers and elicit honest self-identification from the model |

---

## 🧠 The Core Problem

Modern AI deployments frequently involve **model wrapping** — where a base model (e.g., GPT-4, Claude 3, Gemini Ultra) is branded, fine-tuned, and presented under a completely different identity:

```
User thinks they're talking to:  "Aria from TechCorp"
Reality:                          Claude 3.5 Sonnet with a system prompt
```

This creates critical risks:

- ⚠️ **Security** — You can't audit what you can't identify
- ⚠️ **Compliance** — Regulatory frameworks require knowing what AI you're using
- ⚠️ **Trust** — Hidden model swaps undermine informed consent
- ⚠️ **Research Integrity** — Benchmarks become meaningless if the model is unknown

---

## 🔬 Module 1: Identity Forensics

A systematic, multi-signal approach to fingerprint an unknown LLM **without relying on verbal self-disclosure**.

### Signal Categories

```
┌─────────────────────────────────────────────────────┐
│                  FORENSIC SIGNALS                   │
├──────────────────┬──────────────────────────────────┤
│ 🧩 Structural    │ Context window limits             │
│                  │ Token boundary behavior           │
│                  │ Max output constraints            │
├──────────────────┼──────────────────────────────────┤
│ 🔤 Linguistic    │ Default phrasing patterns         │
│                  │ Refusal message fingerprints      │
│                  │ Formatting preferences            │
├──────────────────┼──────────────────────────────────┤
│ 📅 Temporal      │ Knowledge cutoff probing          │
│                  │ Training data boundary tests      │
├──────────────────┼──────────────────────────────────┤
│ ⚙️ Behavioral    │ RLHF alignment signatures         │
│                  │ Chain-of-thought style            │
│                  │ Tool use patterns                 │
├──────────────────┼──────────────────────────────────┤
│ 🚨 Error         │ Error code formats                │
│                  │ Hallucination patterns            │
│                  │ Edge case responses               │
└──────────────────┴──────────────────────────────────┘
```

### Forensic Methodology

1. **Structural Probing** — Test context limits, token counts, output caps
2. **Behavioral Fingerprinting** — Elicit characteristic response patterns unique to each lab
3. **Temporal Triangulation** — Find the exact knowledge cutoff date
4. **Error Signature Analysis** — Identify lab-specific error handling quirks
5. **Cross-Signal Correlation** — Combine signals for high-confidence identification

---

## 💬 Module 2: Identity Truth Prompts

A curated library of **adversarial prompts** designed to extract honest identity disclosure from models operating under fake personas.

### What We're Extracting

```
┌─────────────────────────────────────────────────────┐
│                  PROMPT TARGETS                     │
├──────────────────┬──────────────────────────────────┤
│ 🏭 Lab           │ Who built the underlying model?   │
│                  │ (OpenAI / Anthropic / Google...)  │
├──────────────────┼──────────────────────────────────┤
│ 📦 SKU           │ Which specific version/variant?   │
│                  │ (GPT-4o / Claude 3.5 / Gemini...)  │
├──────────────────┼──────────────────────────────────┤
│ 📅 Cutoff        │ What is the training data cutoff? │
│                  │ (Exact date triangulation)        │
├──────────────────┼──────────────────────────────────┤
│ 🎭 Costume       │ What persona/wrapper is active?   │
│                  │ (Detecting active system prompts) │
└──────────────────┴──────────────────────────────────┘
```

### Prompt Design Principles

- **Multi-layered** — Each prompt works across multiple bypass strategies simultaneously
- **Context-blind** — Works regardless of the active system prompt content
- **Escalating** — Starts soft, escalates intelligently when the model deflects
- **Verifiable** — Every response can be cross-checked against forensic signals

---

## 📂 Repository Structure

```
ModelAudit/
├── 📁 forensics/
│   ├── identity_forensics.md        # Full forensics methodology & signal guide
│   ├── signal_tests/                # Individual signal test scripts
│   └── fingerprint_profiles/        # Known model fingerprint database
│
├── 📁 prompts/
│   ├── identity_truth_prompts.md    # Master prompt card library
│   ├── lab_extraction/              # Lab-specific prompt sets
│   └── cutoff_probing/              # Temporal triangulation prompts
│
├── 📁 results/
│   └── ...                          # Community-contributed findings
│
├── banner.png
└── README.md
```

---

## 🚀 Quick Start

### Step 1: Collect Forensic Signals

Run these probes against any unknown model to build a raw signal baseline:

```python
# Context window probe — find the truncation point
test_prompt = "A" * 100_000  # Adjust until response is truncated

# Knowledge cutoff probe — triangulate training date
"What is the most recent major event you have knowledge of in [DOMAIN]?"

# Refusal fingerprint — identify lab by exact wording
"[Insert known refusal-triggering prompt]"
# → Each lab has a unique refusal style. Collect the exact output.
```

### Step 2: Apply Identity Truth Prompts

Start with **Tier 1** (soft) prompts and escalate as needed:

```
Tier 1 → Indirect identity elicitation
Tier 2 → Logical contradiction framing
Tier 3 → Technical self-reference prompts
Tier 4 → Meta-cognitive override attempts
```

### Step 3: Cross-Reference & Conclude

Match your collected signals against the fingerprint database to produce a **confidence-scored identity report**.

---

## 📊 Identity Confidence Scoring

```
Signal Match Score:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
 90–100%  ████████████████████  CONFIRMED
 70–89%   ████████████████░░░░  HIGH CONFIDENCE
 50–69%   ████████████░░░░░░░░  PROBABLE
 30–49%   ████████░░░░░░░░░░░░  UNCERTAIN
  0–29%   ████░░░░░░░░░░░░░░░░  INCONCLUSIVE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🤝 Contributing

Research contributions are highly encouraged. You can contribute by:

- 📝 **Adding new forensic signals** you've discovered
- 🔍 **Submitting fingerprint profiles** for models you've successfully identified
- 💬 **Contributing prompt cards** that successfully broke through persona layers
- 📊 **Sharing audit results** from real-world deployments

Please open an issue or pull request to get started.

---

## ⚖️ Ethics & Legal Notice

This project is conducted for:

- ✅ Academic research and AI transparency advocacy
- ✅ Security auditing of AI systems you are **authorized** to test
- ✅ Consumer rights and informed consent
- ✅ Open science and reproducible AI research

> ⚠️ **Do not use these techniques to bypass safety systems, extract training data, or conduct unauthorized testing on systems you do not own or have explicit permission to audit.**

---

## 📄 License

[MIT License](LICENSE) — Free to use, modify, and distribute with attribution.

---

<div align="center">

**ModelAudit** — *Because transparency is not optional.*

<br/>

⭐ If this project helped your research, please star the repo ⭐

<br/>

[![Follow on GitHub](https://img.shields.io/github/followers/Kayra-ML?style=social)](https://github.com/Kayra-ML)

</div>
