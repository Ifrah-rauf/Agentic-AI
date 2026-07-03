<!-- ====================================================== -->
<!--                     PAGE HEADER                         -->
<!-- ====================================================== -->

<div align="center">

# Build Your First LLM Product

### <span style="color:#3B82F6">Part 1 · Foundations of Large Language Models</span>

</div>

---

> **Topics Covered**
>
> - What LLMs struggle with
> - Frontier Models
> - Foundation Models
> - GPT
> - From LSTMs → Transformers
> - Tokens & Context
> - LLM to build Sales Brochure for a company
---

<br>

# What LLMs Struggle With

<img src="static/i1.png" width="850"/>

<br>

## Hallucinations

> **Definition**
Hallucinations are probably the most talked-about weakness.  An LLM will confidently generate information that sounds completely plausible but is actually false. Tricky part is that the model itself has no real way to distinguish between an answer it's "confident" about and one that's actually "correct”. It’s just predicting likely-sounding text, not checking facts against reality. This tends to get worse in a few predictable situations: when the model simply doesn't have the relevant knowledge, when your prompt is vague or underspecified, or when the reasoning chain required to answer is long and has more room for the model to drift off track. 

**Occurs when**

- Missing knowledge
- Vague prompts
- Long reasoning chains

```text
Mitigation
→ RAG
→ Tool Calling
→ Verification
```

---

## Mathematical Computation
LLMs are fundamentally pattern-predictors, not calculators. They're actually much better at reasoning through a problem conceptually than at doing exact arithmetic. Anything involving large numbers or multiple sequential calculation steps is where things tend to fall apart, since small errors compound. The practical fix is don't make the model do math in its head instead hook it up to an actual calculator or computational tool and let it call that instead.

```text
Use:
Calculator Tool
Python Tool
```

---

## Long Context

As the amount of text in a conversation or document grows, model performance quietly degrades and it may start ignoring instructions you gave early on, or lose track of important details buried somewhere in the middle of a long exchange. This is usually addressed through RAG (pulling in only the relevant chunks rather than dumping everything into context) or summarization (compressing older parts of the conversation) commonly.

```text
Solutions
→ RAG
→ Context Compression
→ Summarization
```

---

## Real-Time Knowledge

A limitation baked into how these models are built. A base model's knowledge is essentially frozen at whatever point its training data was collected. It has no awareness of anything that happened after that cutoff unless it's explicitly connected to external tools like web search. The solution is straightforward: pair the model with web search and RAG so it can pull in current information rather than relying solely on what it learned during training.

```text
Solution
Web Search + RAG
```

---

## Logical Consistency

The same model might give you contradictory answers to related questions, change its stated opinion between prompts, or simply produce outputs that don't line up with each other across a conversation. Temperature (a setting that controls how much randomness goes into the model's word choices) plays a real role here; higher temperature generally means more variation and potentially more inconsistency.

Controlled by:

- Temperature
- Sampling

---

<br>

<hr>

<br>

# Frontier Models

<img src="static/i2.png" width="850"/>

<br>

## Definition

A frontier model refers to the most capable, state-of-the-art foundation models currently available. The ones built using massive amounts of compute and datasets, pushing the boundary of what's possible. GPT, Claude, Gemini, and Grok are the examples people usually point to.  Common characteristic are: these models are general-purpose rather than narrowly specialized, they're multimodal (meaning they can handle more than just text like images, sometimes audio or video too), they support long context windows, they can call external tools, and they tend to show strong reasoning and code generation abilities.

Examples

- GPT
- Claude
- Gemini
- Grok

---

## Characteristics

- General-purpose
- Multimodal
- Long context
- Tool Calling
- Strong reasoning
- Code generation

---

## Foundation Models

A foundation model is a large model that's been pretrained on massive data and then serves as the base layer for a wide range of downstream tasks rather than being built for one narrow purpose, it's general enough to be adapted afterward. Example GPT, Llama, Gemini, Claude, and Qwen. The way we adapt a foundation model to a specific task is either through fine-tuning (further training it on task-specific data) or simply through prompting (guiding its behavior with careful instructions, without changing the underlying model at all).

Examples

- GPT
- Claude
- Gemini
- Llama
- Qwen

Adaptation methods

```text
Foundation Model

     │

 ┌───┴────┐

Prompting
Fine-tuning
```

---

<br>

<hr>

<br>

# GPT

<img src="static/i3.png" width="850"/>

<br>

## GPT = Generative Pre-trained Transformer

---
GPT stands for Generative Pre-trained Transformer, and each of those three words actually describes a distinct part of what the model is.
Generative means the model produces new content rather than just retrieving or classifying existing information including text, code, summaries, SQL queries, and explanations, all generated fresh in response to a prompt.
Pre-trained refers to the fact that the model learns general language patterns from massive datasets before it ever interacts with a real user. During this phase, it picks up grammar, reasoning patterns, factual knowledge, programming syntax, and an understanding of how concepts relate to one another all before any fine-tuning or deployment happens.
Transformer is the underlying architecture that makes all of this possible, introduced back in 2017 in the paper "Attention Is All You Need” created by Google researchers It replaced RNNs and LSTMs (the older architectures used for sequential data) for most natural language processing tasks, largely because of its attention mechanism, which lets the model weigh the relevance of different words to each other regardless of their distance in the text.


---

<br>

<hr>

<br>

# From LSTMs → Transformers

<img src="static/i4.png" width="850"/>

<br>

## LSTM

```text
Word1
 ↓
Word2
 ↓
Word3
 ↓
Word4
```

Properties

- Sequential
- Slow
- Poor long-range memory
- Difficult to parallelize

---

## Transformer

```text
A ─────┐
B ──┬──┼──┐
C ──┼──┼──┤
D ──┴──┴──┘
```

Properties

- Parallel processing
- Self-attention
- Better long-context understanding
- Highly scalable

---

## Self-Attention

Each token attends to every other token.

Example

```text
"The animal didn't cross the road because it was tired."

          │
          ▼
        "it"

attends to

      animal
```

---

## Comparison

| LSTM | Transformer |
|------|-------------|
| Sequential | Parallel |
| Slow | Fast |
| Hidden State | Self-Attention |
| Weak Long Memory | Better Long Dependencies |
| Difficult Scaling | Billion+ Parameters |

---

<br>

<hr>

<br>

# Summary

| Topic | Key Point |
|--------|-----------|
| Hallucination | Plausible but false output |
| Long Context | Earlier context degrades |
| Frontier Model | State-of-the-art foundation model |
| Foundation Model | Base pretrained model |
| GPT | Generative + Pre-trained + Transformer |
| Transformer | Introduced in 2017 |
| LSTM | Sequential architecture |
| Self-Attention | Every token attends to others |

---

<div align="center">

### Next → Tokens • Context Window • Parameters • Inference

</div>
