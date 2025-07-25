---
title: "AdvProb: Adversarial Probes to Test Confidence Robustness in Out-of-Distribution Detection"
authors:
  - Philippe Bergna
  - Jake Thomas
date: "2025-06-01T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2025-06-01T00:00:00Z"

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
  - name: Preprint Link
    url: 'https://arxiv.org/abs/2408.16115' # Replace with the actual preprint link

url_code: 'https://github.com/RichardBergna/GraphNeuralSDE'
url_project: ''
url_slides: ''
url_source: '#'

image:
  caption: 'AdvProb: Adversarial Probes to Test Confidence Robustness in Out-of-Distribution Detection
  focal_point: ""
  preview_only: false

projects:
  - graph-uncertainty

slides: ""
---

This work provides a framework for leveraging stochastic differential equations to address uncertainty in graph neural networks, positioning it as a key approach for robust, uncertainty-aware models in structured data applications.
