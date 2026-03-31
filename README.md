# Parameter Golf — OpenAI Model Craft Challenge Submission

> A research project exploring co-designed tiny language models 
> optimised for bits-per-byte compression under strict size and 
> training constraints.

---

## Challenge Constraints

| Constraint | Limit |
|---|---|
| Model + code size | ≤ 16MB |
| Training time | ≤ 10 minutes on 8×H100 |
| Dataset | FineWeb (fixed) |
| Metric | Bits per byte (BPB) — lower is better |

---

## Our Approach

Most efficient model research treats size and speed as 
post-training concerns. We flip that — making compression 
efficiency the primary design objective from architecture 
inception.

Three core ideas driving the design:

1. **Co-design** — architecture, quantisation, and training 
   objective designed jointly, not sequentially
2. **Short training as a feature** — 10-minute constraint 
   makes weights naturally robust to aggressive quantisation
3. **MLP ratio as a design lever** — reducing expansion ratio 
   from standard 4× to 2.5× frees parameter budget for depth

---

## Architecture (EffNet-16)

| Component | Choice | Reason |
|---|---|---|
| Tokenisation | Byte-level, vocab 1024 | No external tokeniser needed |
| Layers | 12 | Depth beats width at tiny scale |
| Hidden dim | 480 | Balanced parameter budget |
| Attention | 8 heads, 4 KV (GQA) | Half cost, near-full quality |
| MLP expansion | 2.5× | Novel lever — frees budget for depth |
| Weight tying | Yes | Free compression |
| Positional enc | RoPE | Zero parameters, better generalisation |
| Quantisation | INT6 QAT + STE | Sweet spot between INT4 and INT8 |
| Est. parameters | ~16M | |
| Est. size | ~12MB weights | |

---

## Repository Structure
```
parameter-golf/
├── weights/             # trained model weights
├── config/              # model configuration
│   └── config.json
├── train.py             # training script
├── run.sh               # execution script
├── training_log.txt     # training run log
└── README.md
```

---

## About This Project

This submission is part of a structured learning project. 
The author is an early-stage data science learner building 
real research skills through a live competition — covering 
literature review, architecture design, experimental 
methodology, implementation, and academic writing in parallel.

The goal is not just to compete, but to understand every 
design decision deeply enough to write about it rigorously.

---

## Licence

MIT
```

Click **Commit changes** → commit directly to main branch.

---

## 2. How to Apply for OpenAI Compute Credits

Step by step:

**Step 1:** Go to this exact URL:
```
https://openai.com/index/parameter-golf
```

**Step 2:** Scroll down until you see a section that says something like *"Request compute credits"* or *"Apply for credits."* Click that button or link.

**Step 3:** You'll see a form. Fill it in like this:
```
Name:          [Your real full name]

Email:         [Your email address]

GitHub:        https://github.com/Danrangi/parameter-golf

Description:   I am an early-stage data science learner from Nigeria 
               participating in the Parameter Golf Challenge as a 
               structured learning project. I am working on a novel 
               co-designed tiny language model (EffNet-16) that jointly 
               optimises architecture, INT6 quantisation-aware training, 
               and bits-per-byte compression under the 16MB constraint. 
               This is my first real research and implementation project 
               and I am committed to a full submission including model 
               weights, training code, and a technical write-up.
