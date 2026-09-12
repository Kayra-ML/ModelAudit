<div align="center">

<img src="banner.png" alt="Model Audit Banner" width="100%"/>

<br/><br/>

# Model Audit

### LLM Identity Forensics & Transparency Verification Framework

*Cutting through the costume. Exposing the core.*

---

</div>

## What Is This?

**ModelAudit** is an open research framework for **verifying the true identity of Large Language Models (LLMs)** — regardless of what name, persona, or "costume" they are presented under.

When you access an AI assistant through an API or a product, you are often told *what* the model is supposed to be. But is it? This project provides the tools and methodology to find out.

It operates on two fronts:

| Module | Purpose |
|--------|---------|
| 🔬 [`_IDENTITY-FINGERPRINT.md`](_IDENTITY-FINGERPRINT.md) | Detect the real model through technical signals — context window, tokenizer artifacts, error patterns, latency fingerprints, behavioral biases |
| 💬 [`_IDENTITY-TRUTH-PROMPTS.md`](_IDENTITY-TRUTH-PROMPTS.md) | Adversarial prompts that bypass persona layers and elicit honest self-identification from the model |

---

## The Core Problem

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

## Module 1: Identity Forensics

→ Full methodology in [`_IDENTITY-FINGERPRINT.md`](_IDENTITY-FINGERPRINT.md)

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

## Module 2: Identity Truth Prompts

→ Full prompt card library in [`_IDENTITY-TRUTH-PROMPTS.md`](_IDENTITY-TRUTH-PROMPTS.md)

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

## Identity Confidence Scoring

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

## Lab Cheat Sheet (2026 Field)

| If you see… | Hypothesize |
|-------------|-------------|
| Exact Anthropic error types + XML tools + constitutional refuse | Anthropic serving |
| `system_fingerprint`, `finish_reason=stop`, `reasoning` field | OpenAI serving |
| `prompt_tokens` CJK matches Google tokenizer + grounding | Gemini |
| Error `1301` / Zhipu usage shape | GLM |
| Must-think every turn + DashScope errors | Qwen 2.4T-class |
| `reasoning_content` + cheap API + 中文 | DeepSeek R1/V4 |
| Long continuation addiction, 月之暗面 leaks | Kimi |
| xAI eval cadence, weak product-copy refuse | Grok |
| Llama Guard 400 + ChatML offset | Llama 4 + Guard wrapper |
| le Chat FR safety + tekken template | Mistral |
| Tokenizer=GLM, persona=Claude | **reseller costume** |
| Split-half JSD high | **rotating aggregator** |

---

<div align="center">

**ModelAudit** — *Because transparency is not optional.*

</div>
