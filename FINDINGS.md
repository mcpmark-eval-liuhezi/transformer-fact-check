# Fact-Check Brief: "Attention Is All You Need" (arXiv 1706.03762)

Reading-group session — verification of three claims from the circulating draft, checked
against the paper's abstract (arXiv LaTeX source) and its Results section (Section 6),
then re-confirmed against the official arXiv PDF.

Paper: "Attention Is All You Need" — Vaswani, Shazeer, Parmar, Uszkoreit, Jones, Gomez,
Kaiser, Polosukhin (NIPS 2017). arXiv:1706.03762 (v7, cs.CL).

---

## Claim-by-Claim Verdicts

### Claim 1 — "reports 28.4 BLEU on the WMT 2014 English-to-German translation task"

**Verdict: CONFIRMED**

- **Abstract:** "Our model achieves 28.4 BLEU on the WMT 2014 English-to-German translation
  task, improving over the existing best results, including ensembles, by over 2 BLEU."
  (PDF page 1)
- **Results, Section 6.1 (Machine Translation):** "the big transformer model (Transformer
  (big) in Table 2) outperforms the best previously reported models (including ensembles)
  by more than 2.0 BLEU, establishing a new state-of-the-art BLEU score of 28.4."
  (PDF page 8)
- **Table 2 (PDF page 8):** Transformer (big) — EN-DE **28.4** BLEU.

### Claim 2 — "reports a single-model state-of-the-art score of 41.8 BLEU on WMT 2014 English-to-French"

**Verdict: CONFIRMED**

- **Abstract:** "On the WMT 2014 English-to-French translation task, our model establishes a
  new single-model state-of-the-art BLEU score of 41.8 after training for 3.5 days on eight
  GPUs, a small fraction of the training costs of the best models from the literature."
  (PDF page 1)
- **Results, Section 6.1 (Machine Translation):** "our big model achieves a BLEU score of
  41.0, outperforming all of the previously published single models, at less than 1/4 the
  training cost of the previous state-of-the-art model." (PDF page 8)
- **Table 2 (PDF page 8):** Transformer (big) — EN-FR **41.8** BLEU.

> Reading-group note: Section 6.1's body text quotes 41.0 for the EN-FR big model, while the
> abstract and Table 2 both state 41.8. The headline number to use is **41.8** — it is what
> the abstract claims as the single-model state of the art and what Table 2 records. The
> 41.0 figure in the prose should be treated as an internal inconsistency in the paper text,
> worth flagging in discussion.

### Claim 3 — "the big model was trained for 3.5 days on eight GPUs"

**Verdict: CONFIRMED (with a precision note)**

- **Abstract:** "...after training for 3.5 days on eight GPUs..." (PDF page 1)
- **Results, Section 6.1 (Machine Translation):** "Training took 3.5 days on 8 P100 GPUs."
  (PDF page 8)

> Precision note: the paper specifies the GPUs were **P100** units, and Section 6.1 ties this
> 3.5-day / 8-GPU budget to the *big model*. The draft's claim is accurate as stated.

---

## BLEU Mentions in the Official arXiv PDF

Pages mentioning BLEU (v7 PDF, 15 pages total): **page 1**, **page 8**, **page 9**.

- Page 1 — abstract (28.4 EN-DE; 41.8 EN-FR single-model SOTA; 3.5 days / 8 GPUs).
- Page 8 — main results table **Table 2** appears here, together with the Section 6.1
  (Machine Translation) discussion of both headline scores.
- Page 9 — Table 3 (Model Variations): dev-set (newstest2013) BLEU per configuration, plus
  the Section 6.2 discussion of attention-head variations.

**Table 2 (main results table) is on PDF page 8.**

## Two-Page Excerpt

Saved in the workspace as `transformer_results_excerpt.pdf` — title page (page 1) followed by
the Table 2 page (page 8). Spot-check contents:
- Title: "Attention Is All You Need" ✔
- Author line: Ashish Vaswani (first author, Google Brain; Noam Shazeer, Niki Parmar,
  Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Łukasz Kaiser, Illia Polosukhin) ✔
- 28.4 BLEU and 41.8 ✔
- Table 2 (main results) ✔

---

## Where the Architecture Went: google-bert/bert-base-uncased

Looked up on Hugging Face (model card: https://hf.co/google-bert/bert-base-uncased).

- **Task tag:** `fill-mask` — confirmed.
- **Model card tags include `arxiv:1810.04805`** — the BERT paper (Devlin et al.,
  "BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding") — confirmed.
- **Downloads at time of lookup:** **3268.9M** (≈3.27 billion; 3,043 likes).

BERT inherits the Transformer's encoder-only architecture (self-attention, dispensed
recurrence/convolutions) and adds masked-language-model pre-training — which is exactly
what the `fill-mask` task tag reflects.

---

## Summary Table

| # | Claim | Verdict | Verified in |
|---|-------|---------|-------------|
| 1 | 28.4 BLEU, WMT 2014 EN-DE | Confirmed | Abstract (p.1); Sec 6.1 + Table 2 (p.8) |
| 2 | 41.8 BLEU single-model SOTA, WMT 2014 EN-FR | Confirmed | Abstract (p.1); Table 2 (p.8); note Sec 6.1 prose says 41.0 |
| 3 | Big model trained 3.5 days on eight GPUs | Confirmed | Abstract (p.1); Sec 6.1 (p.8) — P100 GPUs |

All three claims in the circulating draft are accurate as stated.
