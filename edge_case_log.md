# Edge Case Log
## Customer Review Sentiment Annotation Project — v1.0

This document records every review that required extra deliberation during annotation, the options considered, and the final decision with reasoning.

---

### Edge Case 001 — Faint Praise
**Review ID:** 73
**Review:** "It is not the worst thing I have bought."
**Options considered:**
- Neutral — the reviewer is not complaining and not praising
- Slightly Positive — avoiding negative could imply mild satisfaction

**Decision:** Neutral
**Reasoning:** Faint praise that avoids negativity does not constitute a positive experience. The reviewer did not express satisfaction, only the absence of extreme dissatisfaction. Per guidelines: no enthusiasm = no Positive label.

---

### Edge Case 002 — Mixed Review with Positive Product but Negative Shipping
**Review ID:** 29
**Review:** "Great product but delivery took forever."
**Options considered:**
- Positive — the core product is praised
- Negative — delivery failure is significant
- Neutral — two equal-weight signals cancel out

**Decision:** Neutral
**Reasoning:** "Great product" and "delivery took forever" represent equally weighted opposing signals. The product is the primary reason for purchase, but shipping failure significantly impacts overall experience. Neither dimension dominates, so Neutral is appropriate.

---

### Edge Case 003 — Fast Shipping + Poor Product
**Review ID:** 12
**Review:** "Fast shipping but the product quality is very poor."
**Options considered:**
- Neutral — one positive, one negative
- Negative — core product failure outweighs logistics

**Decision:** Negative
**Reasoning:** Unlike Case 002, here the product quality is described as "very poor." A fast shipping experience cannot redeem a defective core product. Product quality carries more weight than logistics. This differs from Case 002 where the product was "great."

---

### Edge Case 004 — Sarcasm Detection
**Review ID:** 11
**Review:** "Oh sure the product is AMAZING. Fell apart in two days."
**Options considered:**
- Positive — surface reading of "AMAZING"
- Negative — actual meaning after sarcasm resolution

**Decision:** Negative, Sarcasm: Yes
**Reasoning:** "Oh sure" is a classic sarcasm marker. ALL CAPS intensifies irony. The second sentence confirms the true meaning. Surface label would be incorrect. Always resolve sarcasm before assigning sentiment.

---

### Edge Case 005 — Informational Complaint vs Sentiment
**Review ID:** 28
**Review:** "The size runs a bit small. I would suggest sizing up."
**Options considered:**
- Negative — identifies a product flaw
- Neutral — the reviewer is offering helpful advice, not expressing frustration

**Decision:** Neutral (Medium confidence)
**Reasoning:** The review is informational and advisory in tone. "A bit small" is a mild factual observation. The reviewer does not express disappointment or frustration — they offer constructive guidance. No strong negative emotional language present.

---

### Edge Case 006 — Third-Party Positive Sentiment
**Review ID:** 56
**Review:** "I gifted this to my mom and she absolutely loves it."
**Options considered:**
- Positive — clear love expressed
- Neutral — the reviewer is not the end user

**Decision:** Positive
**Reasoning:** The reviewer chose to purchase and gift the item, and reports a strong positive reaction from the recipient. The reviewer's implicit satisfaction (choosing to gift it, reporting the outcome positively) qualifies as positive sentiment even if indirect.

---

### Edge Case 007 — Segment-Dependent Review
**Review ID:** 54
**Review:** "Great for beginners but advanced users may want more features."
**Options considered:**
- Positive — "great for beginners"
- Neutral — the praise is conditional on user type

**Decision:** Neutral (Medium confidence)
**Reasoning:** The positive label depends entirely on who is reading. For a beginner this is positive; for an advanced user it is slightly negative. Since the reviewer does not identify their own user type and the sentiment depends on unknown context, Neutral is appropriate.

---

### Edge Case 008 — Implied Designed Failure
**Review ID:** 97
**Review:** "Stopped working after exactly 31 days. Right after the return window."
**Options considered:**
- Negative — product failure
- Negative with additional severity — deliberate timing implies fraud

**Decision:** Negative (High confidence)
**Reasoning:** The primary label is Negative due to product failure. The "exactly 31 days / after the return window" detail implies the reviewer suspects deliberate design to fail post-warranty. This is captured in annotator_notes and strengthens the Negative signal without changing the label category. Aspect: Product Durability + After-Sales.

---

### Edge Case 009 — Minimal Engagement
**Review ID:** 42
**Review:** "Whatever. It arrived."
**Options considered:**
- Neutral — no sentiment words
- Slightly Negative — "whatever" implies indifference or mild frustration

**Decision:** Neutral (Medium confidence)
**Reasoning:** "Whatever" could signal mild frustration but also pure indifference. The bare statement "It arrived" offers no quality or experience signal. Absence of praise does not equal negative. Labeled Neutral; the medium confidence reflects the ambiguity of "whatever."

---

### Edge Case 010 — Hedged Positive
**Review ID:** 51
**Review:** "Pretty good. Would probably buy again if needed."
**Options considered:**
- Neutral — hedged language throughout
- Positive — repurchase intent is a positive signal

**Decision:** Positive (Medium confidence)
**Reasoning:** "Would probably buy again" is a conditional repurchase signal which indicates satisfaction. The hedged language ("pretty good", "probably", "if needed") reduces confidence but does not eliminate the positive lean. Medium confidence reflects the hedging.

---

### Edge Case 011 — Price-Origin Comment
**Review ID:** 53
**Review:** "The product is made in China."
**Options considered:**
- Neutral — purely factual
- Negative — some readers may interpret country of origin as a quality signal

**Decision:** Neutral (High confidence)
**Reasoning:** Per guidelines, country of origin statements are always Neutral regardless of how some readers might interpret them. The reviewer stated a fact without attaching sentiment. No signal words present.

---

### Edge Case 012 — Implicit Satisfaction
**Review ID:** 35
**Review:** "Came exactly as described. No surprises."
**Options considered:**
- Neutral — factual delivery confirmation
- Positive — matching the listing is a positive outcome for buyers

**Decision:** Positive (Medium confidence)
**Reasoning:** For online shoppers, receiving an item that matches its listing exactly is a genuinely positive outcome — it is what is expected and frequently violated. "No surprises" signals relief and satisfaction. Medium confidence because the language is understated.

---

## Summary Statistics

| Total reviews | 100 |
|---|---|
| Edge cases logged | 12 |
| Sarcasm cases | 3 (IDs: 11, 22, 60) |
| Confidence: High | 78 |
| Confidence: Medium | 22 |
| Confidence: Low | 0 |

