# Women in the Nobel Prize: Recognition, Growth, and the Fields Left Behind

## Overview

This project investigates how women have been recognized in the Nobel Prize 
across categories and over time, and whether early recognition in a field 
was followed by sustained growth in female representation, or remained an 
isolated event.

The analysis is descriptive and structural. No causal claims are made.

---

## The Question

Do Nobel Prize categories differ in how female recognition has evolved over time?
Specifically: after the first woman wins in a given field, does recognition grow, 
stagnate, or remain sporadic?

---

## The Argument

Early female recognition in a Nobel category acts as a structural signal.
In some fields, this signal is followed by sustained growth in female 
representation. In others, recognition remains isolated — suggesting the 
initial signal was not sufficient to trigger a self-reinforcing pattern.

Three outcomes are tested for:

| Loop Type | Description |
|---|---|
| Strong loop | Recognition is followed by increasing female wins over time |
| Broken loop | Recognition occurs but is not followed by growth |
| Lagged loop | Growth eventually appears but is delayed by decades |

---

## What I Found

| Category | Loop Type |
|---|---|
| Literature | ✅ Strong loop |
| Physiology or Medicine | ⏳ Lagged loop |
| Chemistry | ⚠️ Broken loop (possible recent inflection) |
| Physics | ❌ Broken loop |
| Economic Sciences | ❓ Insufficient data |
| Peace | — Excluded (structurally incomparable) |

Physics recognized a woman in 1903 — second only to Peace — yet produced 
the most broken loop in the dataset. Physiology or Medicine waited 46 years 
for its first female winner, yet produced the only STEM field with genuine 
sustained growth.

**Early recognition was not sufficient. What determined the loop was not 
the timing of the first signal — but whether the institutional environment 
was capable of receiving it.**

---

## How I Approached It

### The Missing Gender Problem
24% of gender values were missing in the raw dataset. Rather than ignoring 
this or blindly imputing it, I used a two-track approach:

- **Track 1** — Observed gender only (conservative baseline)
- **Track 2** — Gender inferred via the Genderize API at 90% confidence 
  threshold (primary analysis)

Findings stable across both tracks are treated as robust. Findings that 
shift between tracks are flagged. Inference had meaningful impact only in 
Physiology or Medicine (+37.5% female count) — conclusions in that category 
are treated with appropriate caution.

Gender inference was not applied to Peace Prize winners, as that category 
includes organizations which cannot be gender-inferred from a first name.

---

## Tools & Libraries

- Python 3
- Pandas
- Matplotlib
- Requests (Genderize API)
- Jupyter Notebook

---

## View the Notebook

## View the Notebook

[View on GitHub]([https://github.com/nhdben/nobel-prize-women/blob/main/nobel_women_recognition.ipynb](https://github.com/nhdben/Nobel-prize-gender-analysis/blob/main/nobel_women_recognition.ipynb))

---

## Dataset

The dataset contains one row per Nobel Prize laureate with the following fields:

| Column | Description |
|---|---|
| `award_year` | Year the prize was awarded |
| `category` | Nobel Prize category |
| `full_name` / `known_name` | Laureate's full and commonly known name |
| `sex` | Gender (24% missing — addressed via two-track methodology) |
| `portion` | Share of the prize received |
| `is_shared` | Whether the prize was shared that year |
| `is_repeat_winner` | Whether the laureate won more than once |
| `winners_per_year` | Total winners in that award year |
| `motivation` | Official prize motivation text |
| `birth_country` / `birth_city` | Laureate's origin |
| `affiliation_name` / `affiliation_country` | Institutional affiliation at time of award |
| `prize_amount` / `prize_amount_adjusted` | Prize value (nominal and adjusted) |
| `wikipedia_url` | Link to laureate's Wikipedia page |
---

## What This Data Cannot Tell Us

- The dataset contains winners only, not nominees or contributors
- Small female sample sizes in Physics, Economics, and Chemistry 
  limit interpretability in those categories
- Gender inference introduces uncertainty, addressed via two-track design
- The Nobel Prize reflects institutional recognition patterns, 
  not scientific contribution
- Causality cannot be established from this data
