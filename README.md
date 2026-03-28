# dsrm-reliability-mapping
Disagreement-and-Support Reliability Mapping for Point Cloud Completion

Supplementary results for a paper submitted to eCAADe 2026.

## Method Overview

DSRM is a training-free method that assigns per-point reliability 
scores to completed building point clouds by combining two cues:

- **Disagreement**: inter-model variance across an ensemble of 
  completion networks (proxy for epistemic uncertainty)
- **Support distance**: distance from each completed point to the 
  original partial scan (proxy for extrapolation extent)

The fused scores produce a three-class reliability map:
- 🟢 **Measured**: scan-supported regions
- 🟠 **Reliable completion**: r ≥ 0.5
- 🔵 **Unreliable completion**: r < 0.5 → re-scan recommended

## Dataset

16 self-collected indoor scenes across four building types:
- Residential (8 scenes): 8–15 m × 10–18 m × 3.3–3.5 m
- Public space (6 scenes)
- Office building (1 scene): up to 88.6 m × 56.6 m
- Industrial plant (1 scene)

All coordinates in millimetre units.

## Quantitative Results

| Metric | Value |
|--------|-------|
| Mean AUROC | 0.827 ± 0.055 |
| Mean error ratio (low / high reliability) | 5.77× |
| Mean error (high-reliability regions) | 291 mm |
| Mean error (low-reliability regions) | 1,633 mm |

## Per-Scene Results

### AUROC and Error Ratio
![AUROC per scene](paper_auroc_per_scene.png)
![Error ratio per scene](paper_error_ratio.png)

### Reliability vs. Reconstruction Error (scatter plots)

| Scene | Type | AUROC | Scatter plot |
|-------|------|-------|-------------|
| 0 | Residential | 0.774 |
| 1 | Residential | 0.822 | 
| 2 | Residential | 0.822 |
| 3 | Residential | 0.797 |
| 4 | Residential | 0.798 | 
| 5 | Residential | 0.785 |
| 6 | Residential | 0.772 |
| 75 | Residential | 0.806 |
| pub1 | Public corridor | 0.912 |
| pub2 | Public space | 0.810 |
| pub3 | Public space | 0.871 |
| pub4 | Office building | 0.722 |
| pub5 | Industrial plant | 0.874 |
| pub6 | Public space | 0.868 |
| pub7 | Public space | 0.911 |
| pub8 | Public space | 0.885 |

## Note

Full details of the method, experimental setup, and analysis 
are provided in the submitted paper. This repository contains 
supplementary visualisation results only.

*Author information withheld for double-blind review.*
