# Chimp Test: Effect of House Music on Visual Memory

This is a designed experiment and statistical analysis investigating whether background house music affects performance on the [Chimp Test](https://humanbenchmark.com/tests/chimp) among UCSB undergraduate students. The study used a Randomized Complete Block Design (RCBD) with 30 participants, each completing the test under both conditions (silence and house music). It covers experimental design, paired analysis, RCBD ANOVA, and blocking validation.

## Table of Contents

- [Why Did I Build This?](#why-did-i-build-this)
- [Results](#results)
- [Outline & Analysis](#outline--analysis)
- [Rendered PDF](#rendered-pdf)
- [Dependencies](#dependencies)
- [Acknowledgements & References](#acknowledgements--references)

## Why Did I Build This?

I built this for a Design and Analysis of Experiments upper division elective course during my third year at UCSB as a Statistics and Data Science major. This was a collaborative final project completed with two partners and received full credit for experimental design, design justification, statistical analysis, interpretation, data visualizations, formatted markdown, and overall write up quality. The course covered the statistical theory and application of designed experiments including CRD, RCBD, factorial designs, blocking, and more. The analysis was conducted in R using Quarto and compiled to PDF.

## Results

| Analysis | Statistic | p-value |
|---|---|---|
| Paired t-test | t(29) = 4.84 | 3.94 × 10⁻⁵ |
| RCBD ANOVA — Music | F(1, 29) = 23.44 | 3.94 × 10⁻⁵ |
| RCBD ANOVA — Participant (Block) | F(29, 29) = 7.33 | 3.54 × 10⁻⁷ |

**Condition Means:**
| Condition | Mean Score | SD |
|---|---|---|
| Silence | 11.4 | 2.74 |
| House Music | 9.9 | 2.12 |
| Paired Difference (Silence − Music) | 1.5 | 1.70 |

**Key Finding**
- Participants scored significantly higher in silence than with house music:
    - Mean paired difference: 1.5 levels higher in silence
    - 95% CI for true mean difference: (0.87, 2.13)
    - Both paired t-test and RCBD ANOVA confirm the effect at α = 0.05

## Outline & Analysis

For full code, statistical output, visualizations, and written interpretations, see the [main file](main.QMD). For a brief outline, see below. And for full rendered PDF report, scroll down or [click here](Rendered%20PDF.pdf).

### Part 1 — Introduction & Research Question
- Research question: does house music affect Chimp Test performance vs. silence?
- Response variable: highest level reached before the first strike/failure
- One treatment factor (music condition) with two levels: silence and house music
- RCBD chosen to control for natural variation in memory ability across students

### Part 2 — Experimental Design
- 30 UCSB undergraduate students recruited via convenience sampling (30 blocks)
- Each participant completed both treatment conditions → 60 total observations
- Treatment order randomized across participants to reduce order effects (practice, fatigue)
- Standardized conditions: same laptop + trackpad, same headphones, seated, same music track and volume, two practice rounds before recorded trial

### Part 3 — Exploratory Data Analysis
- Summary statistics by condition with mean, SD, min, max
- Side by side boxplots comparing score distributions across conditions
- Histogram of paired differences (Silence − Music) showing most participants scored higher in silence

### Part 4 — Hypothesis Testing
- Null hypothesis: μ_d = 0 (no mean difference between conditions)
- Paired t-test: t(29) = 4.84, p = 3.94 × 10⁻⁵ → reject H₀
- 95% CI: (0.87, 2.13) — does not include zero, supports the treatment effect

### Part 5 — RCBD ANOVA
- Model: Score ~ Music + Participant ID
- Music factor highly significant (p < 0.001), confirming treatment effect
- Participant blocking factor also highly significant (p < 0.001), validating the RCBD design choice as blocking meaningfully reduced unexplained error variance

### Part 6 — Conclusions & Limitations
- Strong evidence that house music reduces Chimp Test performance by ~1.5 levels on average
- Convenience sampling limits generalizability to all UCSB undergraduates
- No time restriction per question, faster vs. slower pacing may have inflated some scores
- Future work: larger/random sample, time limits per question, multiple music genres

## Rendered PDF

To view the rendered PDF from the [main file](main.QMD) that is produced, [click here](Rendered%20PDF.pdf).

## Dependencies

```r
library(readxl)
library(knitr)
library(kableExtra)
library(ggplot2)
library(patchwork)
```

## Acknowledgements & References

- **[Chimp Test](https://humanbenchmark.com/tests/chimp)** — The visual memory task used as the response measure where participants played until their first strike/failure
- **[Seeing & Believing — Kolter Remix](https://www.youtube.com/watch?v=cWMm28piiBg)** — The house music track (Chris Stussy, Kolter; PIV, 2020) played at a fixed volume for all music- ondition trials
- **[R Project](https://www.r-project.org/)** — The statistical computing language used for all data wrangling, hypothesis testing, ANOVA, and visualization
- **[Quarto](https://quarto.org/)** — The authoring framework used to combine R code, output, and written analysis into a single reproducible PDF report
- **[ggplot2](https://ggplot2.tidyverse.org/)** — Tidyverse package used for boxplots and paired difference histogram
- **[kableExtra](https://cran.r-project.org/web/packages/kableExtra/)** — R package used to format and style data tables in the PDF output
- **[patchwork](https://patchwork.data-imaginist.com/)** — R package used to combine multiple ggplot panels into a single figure layout


**© 2026 Ryan Fabrick. All rights reserved. This project may not be reused, adapted, or submitted for academic coursework without explicit written permission from the author.**

________________________________________________
Built with ❤️ for UCSB

This project demonstrates my interest in experimental design, statistical inference, and applied data and statistcal analysis. It received full credit for an undergraduate course in Design and Analysis of Experiments.