# Sentiment Annotation Guidelines
## Customer Review Sentiment Annotation Project — v1.0

---

## 1. Project Overview

This project annotates customer product reviews across four label dimensions:

| Field | Values |
|---|---|
| Sentiment | Positive / Negative / Neutral |
| Confidence | High / Medium / Low |
| Sarcasm | Yes / No |
| Aspect | Product Quality, Shipping, Customer Service, Value for Money, Product Design, Product Durability, Product Features, Product Comfort, Product Usability, Product Fit, Product Accuracy, Product Origin, Product Reliability, After-Sales, Packaging, Brand, Overall Experience |

---

## 2. Sentiment Label Definitions

### Positive
The review expresses satisfaction, happiness, praise, approval, or enthusiasm.

**Signal words:** love, amazing, excellent, great, highly recommended, best, perfect, fantastic, impressed, exceeded expectations, worth every penny, would buy again

**Examples:**
- "Amazing quality and fast delivery." → Positive
- "Absolutely stunning design. Looks even better in person." → Positive
- "Transformed my morning routine completely." → Positive

**Rule:** If the overall impression is favorable even if one minor complaint exists, label Positive.

---

### Negative
The review expresses dissatisfaction, frustration, complaints, disappointment, or criticism.

**Signal words:** terrible, worst, disappointed, waste, broken, poor quality, stopped working, would not recommend, refund, overpriced, cheap, awful

**Examples:**
- "The item broke after one day of use. Absolutely terrible." → Negative
- "Stopped working after exactly 31 days. Right after the return window." → Negative
- "Charged me twice and still waiting for a refund." → Negative

**Rule:** If the overall impression is unfavorable even if one positive aspect exists, label Negative — provided the positive aspect is minor (fast shipping cannot redeem a broken product).

---

### Neutral
The review is factual, descriptive, ambivalent, or does not clearly lean in either direction.

**Examples:**
- "The color is blue and the size is medium." → Neutral
- "I ordered it on Tuesday and it came Thursday." → Neutral
- "I have mixed feelings. Some things are great, others not so much." → Neutral

**Rule:** Explicitly mixed reviews where positives and negatives are of equal weight are labeled Neutral.

---

## 3. Confidence Label Definitions

| Confidence | When to use |
|---|---|
| High | Label is unambiguous. Signal words are clear. No deliberation needed. |
| Medium | Some ambiguity present. The label is the best choice but another could be argued. |
| Low | Significant ambiguity. Annotator is uncertain. Flag for QA review. |

---

## 4. Sarcasm Detection Rules

Sarcasm flips the surface sentiment. A review that sounds positive on the surface but means the opposite is sarcastic and negative.

**How to detect:**
1. Read the full review, not just the opener
2. Look for contradictions between the praise and the facts stated
3. Look for exaggerated compliments followed by failures
4. Look for ALL CAPS as irony signal
5. Phrases like "oh sure", "yeah right", "totally", "clearly" in an ironic tone

**Examples:**
- "Oh sure the product is AMAZING. Fell apart in two days." → Sarcasm: Yes → Sentiment: Negative
- "Sure this product is flawless. Already broken after three days." → Sarcasm: Yes → Sentiment: Negative

**Rule:** When sarcasm is detected, the sentiment label must reflect the true meaning, not the surface words.

---

## 5. Aspect Label Definitions

| Aspect | What it covers |
|---|---|
| Product Quality | Materials, build, workmanship, general feel |
| Product Durability | Longevity, wear over time, failure rate |
| Product Features | Specific functions, specs, battery, speed |
| Product Design | Appearance, aesthetics, physical form |
| Product Comfort | Ergonomics, wearability, feel in use |
| Product Fit | Size accuracy, sizing guidance |
| Product Usability | Ease of setup, learning curve, intuitiveness |
| Product Accuracy | Match between listing/photos and actual item |
| Product Reliability | Consistency of performance over time |
| Product Origin | Country of manufacture |
| Shipping | Delivery speed, tracking, logistics |
| Packaging | Box condition, presentation |
| Customer Service | Support interactions, responsiveness |
| After-Sales | Returns, refunds, warranty claims |
| Value for Money | Price vs. quality assessment |
| Brand | Brand loyalty, brand-level statements |
| Overall Experience | General holistic statements |

---

## 6. Decision Tree

Step 1 — Check for sarcasm
  Is the opener positive but facts are negative? → Sarcasm: Yes → use true meaning for sentiment
  No contradiction? → Sarcasm: No

Step 2 — Identify aspects mentioned in the review

Step 3 — Determine dominant sentiment
  Does the review praise, recommend, or express satisfaction? → Positive
  Does the review complain, criticize, or express dissatisfaction? → Negative
  Is the review factual, ambivalent, or equally mixed? → Neutral

Step 4 — Assign confidence
  Clear signal words + unambiguous tone → High
  Some ambiguity, one interpretation dominates → Medium
  Genuinely uncertain, could be argued either way → Low

---

## 7. What NOT to do

- Do not assume negative intent from neutral factual statements
- Do not label a review Positive just because it contains one positive word
- Do not label a review Negative just because it contains one complaint
- Do not ignore sarcasm — surface reading is not always correct
- Do not label origin statements (e.g., Made in China) as positive or negative

---

## 8. Annotator Protocol

1. Read the full review before labeling anything
2. Check for sarcasm first
3. Identify aspects
4. Assign sentiment based on dominant tone
5. Assign confidence
6. Write a short reasoning note in the annotator_notes field
7. Flag any Low confidence entries for QA review
