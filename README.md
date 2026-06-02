# joborbot-data

Public Data repo for the [JobOrBot.com](https://joborbot.com) website.

## Overview

This repository contains JSON datasets used by JobOrBot to assess AI exposure across occupations. Each dataset contains the same 342 occupations but with different AI exposure scores and rationales from distinct source methodologies.

## Data Files

All files are located in the [`Data/`](Data/) directory.

### `Data/occupations.json`
**JobOrBot v1 occupation dataset** (342 rows, ~284 KB)

The base occupation catalog with JobOrBot's own editorial AI exposure scoring and rationale layer.

**Sources:**
- [U.S. Bureau of Labor Statistics Occupational Outlook Handbook](https://www.bls.gov/ooh/) — occupation titles, categories, employment numbers, and BLS URLs
- [JobOrBot editorial scoring](https://joborbot.com) — JobOrBot's own occupation-level exposure scoring and rationale

### `Data/karpathy_jobs_v1.json`
**Karpathy Jobs variant** (342 rows, ~268 KB)

AI exposure scores adapted from Andrej Karpathy's jobs repository.

**Sources:**
- [Andrej Karpathy jobs repository](https://github.com/karpathy/jobs)
- [Original scores.json](https://github.com/karpathy/jobs/blob/master/scores.json)

### `Data/anthropic_v1.json`
**Anthropic variant** (342 rows, ~164 KB)

AI exposure scores derived from Anthropic's Economic Index and research on labor market impacts of AI.

**Sources:**
- [Anthropic Economic Index](https://www.anthropic.com/economic-index/)
- [Labor market impacts of AI](https://www.anthropic.com/research/labor-market-impacts)

### `Data/microsoft_ai_v1.json`
**Microsoft AI variant** (342 rows, ~223 KB)

AI exposure scores mapped from Microsoft's AI applicability scores for SOC codes.

**Sources:**
- [Working with AI repository](https://github.com/microsoft/working-with-ai)
- [SOC AI applicability scores CSV](https://github.com/microsoft/working-with-ai/blob/main/soc_ai_applicability_scores.csv)
- [Working with AI paper (arXiv)](https://arxiv.org/abs/2507.07935)

### `Data/manifest.json`
Auto-generated manifest listing all data files with row counts and file sizes.

## Data Schema

Each dataset file follows the same structure:

```json
{
  "dataset": { "id": "...", "label": "..." },
  "sources": [ { "name": "...", "url": "..." } ],
  "rows": [
    {
      "slug": "judges-and-hearing-officers",
      "title": "Judges and hearing officers",
      "category": "legal",
      "category_label": "Legal",
      "jobs": 44800,
      "url": "https://www.bls.gov/ooh/legal/judges-and-hearing-officers.htm",
      "new_exposure": 7,
      "new_rationale": "..."
    }
  ]
}
```

Each row represents one occupation with:
- **slug** — URL-friendly identifier
- **title** — Full occupation title
- **category / category_label** — BLS category classification
- **jobs** — Employment number (from BLS)
- **url** — Link to the BLS Occupational Outlook Handbook page
- **new_exposure** — AI exposure score (1–10 scale, higher = more exposed)
- **new_rationale** — Narrative explanation for the score
