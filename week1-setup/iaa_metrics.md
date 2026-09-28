markdown

# IAA Metrics — Reference and Project Selection

## What is IAA

Inter-Annotator Agreement (IAA) measures how consistently two or more
annotators label the same data. It is a **consistency** metric, not an
**accuracy** metric. Two annotators can agree perfectly and still both
be wrong.

IAA answers one question: **"Is the guideline clear enough that different
people make the same decision?"**

## When to use which metric

| Metric | When to use | Annotators | Data type |
|--------|-------------|------------|-----------|
| Cohen's Kappa | Classification tasks | Exactly 2 | Nominal |
| Krippendorff's Alpha | Multi-annotator, missing data, varied types | 2+ | Nominal / Ordinal / Interval / Ratio |
| IoU | Spatial overlap (BBox, Segmentation) | Pairwise | Spatial |

### Cohen's Kappa
- **Use when**: 2 annotators, classification (positive/negative/neutral)
- **Why not raw agreement %**: Raw agreement ignores chance. If 90% of
  data is one class, two annotators agreeing 95% may still have low Kappa.
- **Good threshold**: κ ≥ 0.61 (substantial), κ ≥ 0.81 (almost perfect)
- **Cannot use when**: 3+ annotators, missing data, ordinal labels

### Krippendorff's Alpha
- **Use when**: 3+ annotators, missing values allowed, or NER/span tasks
- **Difference from Kappa**: Handles missing data, supports more data types
- **Good threshold**: α ≥ 0.80 (reliable), α ≥ 0.667 (exploratory only)
- **Note**: Alpha is stricter than Kappa. Same data often yields lower alpha.

### IoU (Intersection over Union)
- **Use when**: BBox or Segmentation annotation
- **Formula**: IoU = (intersection area) / (union area)
- **Range**: 0.0 (no overlap) to 1.0 (perfect overlap)
- **Good threshold**: Task-dependent
  - COCO detection: ≥ 0.5
  - Autonomous driving: ≥ 0.7
  - Medical imaging: ≥ 0.85
- **Box IoU vs Mask IoU**: BBox uses rectangle area, Segmentation uses pixel-level
- **Cannot use when**: Classification, NER, RLHF (no spatial overlap)

## My project metric selection

This is the declaration I will follow in later weeks.

| Annotation type | Metric | Reason |
|-----------------|--------|--------|
| Classification | Cohen's Kappa | 2 annotators, nominal labels |
| NER | Krippendorff's Alpha | Span-level, 3+ annotators possible |
| BBox | IoU | Spatial overlap, standard for detection |
| Segmentation | Mask IoU | Pixel-level overlap |
| RLHF Preference | Cohen's Kappa | A/B/tie classification, 2 annotators |

## Week 1 note

No actual IAA is computed this week. This file only defines the metric
selection. Real IAA values will be reported in Week 2-5 project READMEs.

## References
- Landis, J.R. & Koch, G.G. (1977). The measurement of observer agreement
  for categorical data. Biometrics, 33(1), 159-174.
- Krippendorff, K. (2004). Content Analysis: An Introduction to Its
  Methodology. Sage Publications.
- COCO Evaluation Metrics: https://cocodataset.org/#detection-eval