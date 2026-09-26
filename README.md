# QinggeLab-AIEOF
Anchored Interventional Equalized-Odds Fairness for Feature Addition

---

## A-IEOF: Anchored Interventional Equalized-Odds Fairness (Feature Addition)

This repository contains the code and experiments for **A-IEOF**, an in-processing fairness framework that  
(i) penalizes **worst-case interventional** Equalized-Odds (EO) gaps on a designated feature block **B**,  
(ii) **anchors** a student to a no-B teacher to preserve legacy behavior, and  
(iii) enforces **stability** of predictions under counterfactual changes to **B**.  
It supports calibrated post-processing with either a single global threshold or **guarded per-group** thresholds.

- **Paper title:** *Anchored Interventional Equalized-Odds Fairness for Feature Addition*  
- **Task:** binary classification with images + tabular metadata  
- **Designated feature block B:** `Institution_le` (categorical; K=10)  
- **Backbone:** MobileNetV2 (ImageNet init)

### ✨ Key ideas

- **Interventional fairness:** measure and shrink EO gaps when **B** is counterfactually replaced  
  `X_B ← b′, b″` (min–max objective).
- **Teacher anchoring:** keep the student with **B** consistent with a strong **no-B** teacher on shared inputs.
- **Stability:** regularize the score change when only **B** changes.
- **Auditable post-processing:** temperature scaling (global or groupwise) + global or per-group thresholds with guardrails.
