# Customer Review Sentiment Annotation Dataset

A multi-layer sentiment annotation project on 100 customer product reviews, built as a data annotation portfolio project demonstrating professional-grade labeling, guideline design, sarcasm detection, and quality assurance.

---

## Project Overview

Most sentiment annotation projects use simple 3-class labels. This project goes further with four annotation dimensions per review:

| Dimension | Description |
|---|---|
| **Sentiment** | Positive / Negative / Neutral |
| **Confidence** | High / Medium / Low |
| **Sarcasm** | Yes / No — detects ironic reversals |
| **Aspect** | What part of the product/experience the review addresses |

This multi-layer approach mirrors what real annotation teams at AI companies produce for training sentiment models used in e-commerce, customer support automation, and brand monitoring.

---

## Dataset Statistics

| Metric | Value |
|---|---|
| Total reviews | 100 |
| Positive | 38 (38%) |
| Negative | 38 (38%) |
| Neutral | 24 (24%) |
| High confidence | 78 (78%) |
| Medium confidence | 22 (22%) |
| Sarcasm cases | 3 (3%) |
| Edge cases documented | 12 |
| Inter-annotator agreement (Cohen's Kappa) | 0.478 (Moderate) |

---

## Project Structure

```
Sentiment-Annotation-Project/
│
├── dataset.csv                    # 100 annotated reviews with all label dimensions
├── annotation_guidelines.md       # Full labeling rules, definitions, decision tree
├── edge_case_log.md               # 12 documented edge cases with reasoning
├── quality_assurance_report.md    # QA process, Cohen's Kappa, disagreement analysis
└── README.md                      # This file
```

---

## File Descriptions

### dataset.csv
The core dataset. Each row is one review with these columns:
- `id` — unique review identifier
- `review` — raw review text
- `sentiment` — Positive / Negative / Neutral
- `confidence` — High / Medium / Low
- `sarcasm` — Yes / No
- `aspect` — what the review is about (single or multi-aspect)
- `annotator_notes` — brief reasoning for the label decision

### annotation_guidelines.md
The complete annotation rulebook used by annotators. Includes:
- Label definitions with signal words and examples
- Sarcasm detection rules
- Aspect taxonomy (17 categories)
- Step-by-step decision tree
- Common mistakes to avoid
- Annotator protocol

### edge_case_log.md
Documents 12 reviews that required extra deliberation. Each entry records:
- The review text
- Options that were considered
- The final decision
- The reasoning

This document shows the depth of thinking behind the labels — the most important thing a hiring team looks for.

### quality_assurance_report.md
Full QA process documentation including:
- Label distribution statistics
- 20-review re-annotation by a second annotator
- Cohen's Kappa calculation (κ = 0.478, Moderate agreement)
- Disagreement analysis for all 6 disagreement cases
- Recommendations for future improvements

---

## Label Examples

### Sarcasm Detection
| Review | Surface | True Label |
|---|---|---|
| "Oh sure the product is AMAZING. Fell apart in two days." | Positive | Negative |
| "Sure this product is flawless. Already broken after three days." | Positive | Negative |

### Ambiguous Neutral Cases
| Review | Why Not Positive | Why Not Negative |
|---|---|---|
| "Works fine I guess." | No enthusiasm, hedged | No complaint expressed |
| "Great product but delivery took forever." | Delivery failure is significant | Product is genuinely praised |
| "It is not the worst thing I have bought." | Faint praise only | No actual complaint |

---

## Tools Used

| Tool | Purpose |
|---|---|
| Google Sheets | Initial annotation and QA comparison |
| Python (pandas) | Dataset export to CSV format |
| GitHub | Portfolio hosting |
| Markdown | Documentation |

---

## Skills Demonstrated

- Multi-dimensional annotation schema design
- Sarcasm and irony detection in text
- Aspect-based sentiment annotation
- Inter-annotator agreement measurement (Cohen's Kappa)
- Edge case documentation and resolution
- Annotation guideline authoring
- Quality assurance process design

---

## How to Use This Dataset

```python
import pandas as pd

df = pd.read_csv('dataset.csv')

# View label distribution
print(df['sentiment'].value_counts())

# Filter sarcasm cases
sarcasm_df = df[df['sarcasm'] == 'Yes']

# Filter by aspect
shipping_df = df[df['aspect'].str.contains('Shipping')]

# Filter medium confidence for review
review_needed = df[df['confidence'] == 'Medium']
```

---

## Author

This dataset was created as a portfolio project for data annotation, AI training, and AI model evaluation roles.
Annotation performed following professional NLP annotation standards with documented inter-annotator agreement.

