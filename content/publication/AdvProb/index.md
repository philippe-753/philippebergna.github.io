---
title: "AdvProb: Adversarial Probes to Test Confidence Robustness in Out-of-Distribution Detection"
authors:
  - Philippe Bergna
  - Jake Thomas
date: "2025-07-15"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2025-07-15"

# Publication type.
publication_types: ["preprint"]

# Publication name and optional abbreviated publication name.
# publication: "Preprint - Currently under review for ICLR 2024"
publication_short: "ICLR (Under Review)"

abstract: |
 Neural networks frequently yield overconfident predictions when encountering out-of-distribution (OOD) samples, undermining their reliability in critical real-world tasks. In this paper, we introduce \textbf{AdvProb:} Adversarial Probes, a novel diagnostic framework for robust OOD detection. Our approach applies multiple targeted adversarial perturbations to each input, systematically probing the local stability of model predictions. By analyzing how model confidence shifts under these perturbations, we construct a comprehensive behavioral fingerprint for each input and train an XGBoost ensemble to robustly discriminate between in-distribution (ID) and OOD data. AdvProb substantially improves the OOD detection performance of standard classifiers and can be seamlessly integrated into existing methods like ODIN and Mahalanobis, yielding consistent performance gains across architectures and datasets. Our results highlight adversarial probes as a flexible and highly effective tool for enhancing OOD detection robustness.

summary: |
  Using adversarial probes as a tool for testing the confidence stability of the model for out-of-distribution OOD detection. 

tags:
  - Out-of-Distribution detection
  - Computer Vision
  - Machine Learning

featured: true

links:
  - name: PDF
    url: OOD_detection_with_adversarial_perturbation.pdf


# url_code: 'https://github.com/RichardBergna/GraphNeuralSDE'
# url_project: ''
# url_slides: ''
# url_source: '#'

image:
  caption: 'AdvProb: Adversarial Probes to Test Confidence Robustness in Out-of-Distribution Detection'
  focal_point: ""
  preview_only: false

projects:
  - CV-OOD

slides: ""
---

This work presents a novel OOD detection method that tests the stability of model confidence using adversarial probes optimized with diverse objectives.

<embed src="OOD_detection_with_adversarial_perturbation.pdf" width="100%" height="800px" type="application/pdf">

