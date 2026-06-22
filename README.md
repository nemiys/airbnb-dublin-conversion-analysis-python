# <img src="https://flagcdn.com/w40/ie.png" width="28"> Airbnb Dublin – Conversion Funnel Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nemiys/airbnb-dublin-conversion-analysis-python/blob/main/airbnb_analysis.ipynb)

## Overview

This project analyzes guest behavior on Airbnb's Dublin marketplace to identify where users drop off in the booking funnel and what drives conversion. The analysis covers ~130,000 search events and ~50,000 contact interactions.

**Core question:** Of all users who search, how many actually book — and why do the others leave?

## Key Findings

| Finding | Insight |
|---|---|
| **Filter users convert 3× more** | Guests who apply price or room-type filters are far more likely to book — filters signal intent |
| **Lead time matters at Accept** | The 8–30 day window has the highest host accept rate; last-minute contacts underperform |
| **Idle listings leak guests** | Hundreds of listings receive contacts but never convert due to very low host accept rates |
| **Ireland anomaly** | IE generates the most searches but one of the lowest conversion rates; host-searcher overlap is a partial but not full explanation |
| **France = efficiency benchmark** | FR users apply filters at the highest rate on the platform — and convert accordingly |
| **US timezone gap** | US guests often contact Dublin hosts during local sleep hours, inflating reply times |

## Funnel Structure

```
Search → Contact → Reply → Accept → Book
```

Each stage counts **unique users** — not row counts. This correctly reflects platform-level funnel attrition rather than per-contact rates.

## Project Structure

```
airbnb-dublin-conversion-analysis-python/
├── airbnb_analysis.ipynb     ← Main analysis notebook
├── contacts_fixed.xlsx       ← Contact events dataset (pre-cleaned)
├── searches_fixed.xlsx       ← Search events dataset (pre-cleaned)
└── Countries.csv             ← Country reference table
```

## Tools & Stack

| Tool | Purpose |
|---|---|
| Python 3 / Pandas | Data wrangling, aggregation, funnel calculation |
| Matplotlib / Seaborn | Visualizations |
| Google Colab | Notebook environment |
| Excel | Initial data cleaning (documented in notebook) |

## Data Cleaning Summary

Performed in Excel before Python analysis:
- Converted timestamp columns from text to datetime
- Replaced literal `"NULL"` strings with true blanks in the Contacts table
- Validated logical consistency (no bookings without prior replies — 0 violations)
- Clipped negative lead-time values (same-day checkins) to 0
- Flagged 25 date-logic errors and 11,849 date-less searches in the Searches table

Full documentation is in the notebook under **Part A – Data Preparation**.

## Business Recommendations

1. **Prompt filter usage** — nudge guests to filter before browsing; it triples conversion rate
2. **Re-engage high-intent searchers** — users with 50+ searches but no booking are high-conversion targets
3. **Educate guests on lead time** — push the 8–30 day booking window across markets
4. **De-rank idle listings** — hosts with accept rates below 30% are wasting guest contacts
5. **Timezone-aware messaging** — tell US guests when to expect a reply from Dublin hosts

---

## Author

**Nemi Yossef Hai** – Data Analyst  
[LinkedIn](https://www.linkedin.com/in/nemi-yossef-hai) · nemiys@gmail.com
