---
title: Aversarial Attacks Introduction
summary: A summary of what are adversariala attacks, the optimisation attacks and more.
date: 2023-10-24
type: docs
math: false
tags:
  - Python
image:
  caption: 'Embed rich media such as videos and LaTeX math'
---



# Introduction to Adversarial Attacks in Computer Vision

*Building Trust and Robustness in AI Models through Understanding Adversarial Vulnerabilities*

---

## Table of Contents
1. [Introduction](#introduction)
2. [What Are Adversarial Attacks?](#what-are-adversarial-attacks)
3. [Why Do Adversarial Attacks Exist?](#why-do-adversarial-attacks-exist)
4. [Types of Adversarial Attacks](#types-of-adversarial-attacks)
5. [Seminal Papers on Adversarial Attacks](#seminal-papers-on-adversarial-attacks)
6. [Conclusion](#conclusion)
7. [Further Reading](#further-reading)

---

## Introduction

For the past 2.5 years, I have been engaged as a research scientist focusing on AI safety for computer vision systems at [Advai](https://www.advai.co.uk/). In recent years, the surge in popularity of Large Language Models (LLMs) such as ChatGPT, Gemini, and Claude has shifted the attention of the AI safety community towards ensuring the reliability and security of these sophisticated language-based systems. However, I contend that research on adversarial attacks in computer vision remains a critical milestone for building trust and developing robust AI models.

Adversarial attacks expose fundamental vulnerabilities in machine learning models, particularly in computer vision, by introducing subtle perturbations to input data that lead to incorrect model predictions. Understanding these attacks is essential not only for enhancing the security of AI systems but also for advancing the overall field of machine learning by highlighting areas where models may fail unexpectedly.

This blog serves as an introductory exploration of adversarial attacks, delving into their definitions, underlying causes, various types, and significant research contributions. Whether you are an AI practitioner, researcher, or enthusiast, this discussion aims to provide a comprehensive foundation for understanding and addressing adversarial vulnerabilities in computer vision systems.

---

## What Are Adversarial Attacks?

Adversarial attacks are intentional manipulations of input data designed to deceive machine learning models into making incorrect predictions or classifications. These manipulations are often imperceptible to humans but can significantly alter the model's output. The phenomenon was first widely recognized in the context of image classification tasks but extends to various domains within machine learning.

### Formal Definition

Given a machine learning model \( f \) that maps input data \( x \) to output predictions \( f(x) \), an adversarial attack seeks to find a perturbed input \( x' \) such that:


$$
x' = x + \delta \quad \text{where} \quad \| \delta \| < \epsilon \quad \text{and} \quad f(x') \neq f(x)
$$


Here, \( \delta \) represents the perturbation added to the original input \( x \), and \( \epsilon \) defines the maximum allowable magnitude of this perturbation, typically measured using norms such as \( \ell_\infty \) or \( \ell_2 \).

### Real-World Implications

Adversarial attacks pose significant risks in applications where AI systems are deployed in safety-critical environments. For instance, in autonomous driving, a minor alteration to a traffic sign could lead to misclassification, resulting in potentially hazardous driving decisions. Similarly, in security systems employing facial recognition, adversarial examples could bypass authentication mechanisms, compromising system integrity.

![Adversarial Example](https://your-image-link.com/adversarial_example.png)  
*Figure 1: An adversarial image where minor alterations deceive the AI into misclassification.*

---

## Why Do Adversarial Attacks Exist?

The existence of adversarial attacks raises profound questions about the nature of machine learning models and their decision-making processes. Despite extensive research, the precise reasons behind the susceptibility of models to such minimal perturbations remain partially understood, making this an active area of investigation.

### Theoretical Perspectives

Several hypotheses have been proposed to explain why adversarial attacks are effective:

1. **High-Dimensional Spaces:** In high-dimensional input spaces, such as images, there exist numerous directions in which input data can be perturbed without significantly altering human perception. This abundance of directions provides adversaries with ample opportunities to find perturbations that mislead models.

2. **Linear Behavior in Non-Linear Models:** Despite the non-linear nature of deep neural networks, these models exhibit locally linear behavior in high-dimensional spaces. This linearity can be exploited by adversaries to craft perturbations using gradient-based methods effectively.

3. **Overfitting to Training Data:** Models that overfit to training data may capture noise and irrelevant patterns, making them more vulnerable to adversarial manipulations that exploit these specific learned patterns.

4. **Model Complexity and Decision Boundaries:** The complexity of model architectures can lead to intricate decision boundaries. Adversarial perturbations can navigate these boundaries to cross into regions associated with different classes with minimal input changes.

### Empirical Evidence

Empirical studies demonstrate that even state-of-the-art models, such as convolutional neural networks (CNNs), are highly susceptible to adversarial attacks. The consistent success of various attack strategies across different models and datasets underscores the pervasive nature of this vulnerability.

### Implications for AI Safety

Understanding the underlying causes of adversarial vulnerabilities is crucial for developing effective defense mechanisms. Addressing these vulnerabilities is essential for ensuring the reliability and safety of AI systems, particularly as they become increasingly integrated into critical applications.

---

## Types of Adversarial Attacks

Adversarial attacks can be categorized based on several criteria, including the attacker's knowledge of the target model, the attack's objective, and the nature of the perturbations. Below, we outline the primary classifications and notable attack methods within each category.

### 1. Based on Knowledge of the Target Model

#### a. White-Box Attacks

In white-box attacks, the adversary has complete access to the target model's architecture, parameters, and gradients. This comprehensive knowledge allows for precise crafting of adversarial examples by leveraging detailed insights into the model's behavior.

**Examples:**
- **Fast Gradient Sign Method (FGSM)**
- **Projected Gradient Descent (PGD)**
- **Carlini & Wagner (C&W) Attack**

#### b. Black-Box Attacks

Black-box attacks operate under the assumption that the adversary has no internal knowledge of the model. Instead, the attacker can only interact with the model through input-output queries. These attacks often rely on surrogate models or query-based strategies to approximate the target model's behavior.

**Examples:**
- **Zeroth-Order Optimization (ZOO)**
- **Transfer-Based Attacks**
- **Boundary Attack**

### 2. Based on the Attack Objective

#### a. Targeted Attacks

Targeted attacks aim to misclassify an input into a specific, predetermined class. The adversary's goal is not merely to cause any misclassification but to ensure the model predicts a particular incorrect label.

**Example:** Altering an image of a "dog" so that the model classifies it as a "cat."

#### b. Untargeted Attacks

Untargeted attacks seek to cause any misclassification without a specific target class in mind. The objective is to disrupt the model's correct predictions, irrespective of the incorrect label assigned.

**Example:** Modifying an image of a "car" so that the model fails to recognize it as a "car," potentially labeling it as any other category.

### 3. Based on the Nature of Perturbations

#### a. Additive Perturbations

Additive perturbations involve adding small, carefully calculated noise to the input data. These perturbations are typically constrained by norm-based bounds (e.g., \( \ell_\infty \), \( \ell_2 \)) to ensure they remain imperceptible to humans.

**Example:** Slightly adjusting pixel values in an image to deceive the model.

#### b. Non-Additive Perturbations

Non-additive perturbations encompass more complex alterations that may involve spatial transformations, geometric modifications, or other non-linear changes to the input data. These perturbations can be more sophisticated and harder to detect.

**Example:** Applying small rotations, translations, or scaling transformations to an image to alter its classification.

### Notable Adversarial Attack Methods

1. **Fast Gradient Sign Method (FGSM):**
   - A one-step attack that perturbs the input in the direction of the gradient of the loss function with respect to the input.
   - Efficient and widely used for generating adversarial examples quickly.

2. **Projected Gradient Descent (PGD):**
   - An iterative extension of FGSM that applies multiple small perturbations, projecting the perturbed input back into the allowed perturbation space after each step.
   - Considered a strong first-order adversary and often used to evaluate model robustness.

3. **Carlini & Wagner (C&W) Attack:**
   - An optimization-based attack that formulates adversarial example generation as a constrained optimization problem.
   - Known for its effectiveness in circumventing many defense mechanisms.

4. **DeepFool:**
   - An iterative attack that seeks the minimal perturbation required to change the model's prediction by moving the input across the decision boundary.
   - Provides insights into the robustness of models by measuring the distance to the decision boundary.

5. **Generative Adversarial Networks (GANs) Based Attacks:**
   - Utilize GANs to generate adversarial examples by training a generator to produce perturbations that deceive the target model.
   - Capable of producing more natural and transferable adversarial examples.

---

## Seminal Papers on Adversarial Attacks

The field of adversarial machine learning has been shaped by numerous influential research papers. Below, we highlight some of the most significant contributions that have advanced our understanding of adversarial attacks and defenses.

1. **[Explaining and Harnessing Adversarial Examples](https://arxiv.org/abs/1412.6572)**  
   *Ian J. Goodfellow, Jonathon Shlens, Christian Szegedy (2014)*  
   This pioneering paper introduced the Fast Gradient Sign Method (FGSM) and explored the underlying reasons for the existence of adversarial examples. It posited that the linearity of neural networks in high-dimensional spaces contributes to their vulnerability.

2. **[Towards Evaluating the Robustness of Neural Networks](https://arxiv.org/abs/1706.06083)**  
   *Aleksander Madry, Aleksandar Makelov, Ludwig Schmidt, Dimitris Tsipras, Adrian Vladu (2017)*  
   The authors conducted a comprehensive evaluation of neural network robustness against adversarial attacks, introducing Projected Gradient Descent (PGD) as a strong adversary and advocating for robust optimization techniques.

3. **[DeepFool: a simple and accurate method to fool deep neural networks](https://arxiv.org/abs/1511.04599)**  
   *Seyed-Mohsen Moosavi-Dezfooli, Alhussein Fawzi, Pascal Frossard (2016)*  
   This paper presented DeepFool, an efficient iterative attack that estimates the minimal perturbation required to misclassify an input, providing a measure of the model's robustness.

4. **[Adversarial Examples Are Not Easily Detected: Bypassing Ten Detection Methods](https://arxiv.org/abs/1705.07263)**  
   *Nicholas Carlini, David Wagner (2017)*  
   The authors demonstrated that many proposed adversarial example detection methods are ineffective, highlighting the persistent challenge of creating robust defenses.

5. **[Generative Adversarial Networks](https://arxiv.org/abs/1406.2661)**  
   *Ian J. Goodfellow et al. (2014)*  
   While not solely focused on adversarial attacks, this foundational paper introduced GANs, which have been instrumental in developing advanced adversarial example generation techniques.

6. **[Adversarial Training for Free!](https://arxiv.org/abs/2002.08218)**  
   *Yinpeng Dong, Fangzhou Liao, Tianyu Pang, Hang Su, Jun Zhu (2020)*  
   This work explores efficient adversarial training methods that enhance model robustness without significantly increasing training time, contributing to practical defense strategies.

7. **[AutoAttack: Reliable Evaluation of Adversarial Robustness](https://arxiv.org/abs/2003.01690)**  
   *Aditi Raghunathan, Aleksander Madry, Andrew Trask (2020)*  
   AutoAttack is introduced as an ensemble of parameter-free attacks that provides a reliable benchmark for evaluating the adversarial robustness of models.

---

## Conclusion

Adversarial attacks represent a critical challenge in the domain of computer vision and broader machine learning applications. Understanding the mechanisms, types, and implications of these attacks is essential for developing robust and secure AI systems. As the AI landscape continues to evolve, ongoing research into adversarial vulnerabilities and defense strategies remains paramount to ensuring the reliability and safety of intelligent systems deployed in real-world scenarios.

In subsequent posts, we will delve deeper into defense mechanisms against adversarial attacks, explore advanced attack strategies, and examine case studies highlighting the practical implications of adversarial robustness in AI systems.

---

## Further Reading

For those interested in further exploring the topic of adversarial attacks and defenses in machine learning, the following resources provide comprehensive insights and detailed methodologies:

- **[Explaining and Harnessing Adversarial Examples](https://arxiv.org/abs/1412.6572)** by Ian Goodfellow et al.
- **[Adversarial Machine Learning](https://www.coursera.org/learn/adversarial-ml)** - Coursera Course
- **[Adversarial Attacks and Defenses: A Comprehensive Survey](https://arxiv.org/abs/2004.00051)** by Akbar et al.
- **[CleverHans Library](https://github.com/cleverhans-lab/cleverhans)** - Tools for Adversarial Learning
- **[Robustness Gym](https://robustnessgym.ai/)** - A toolkit for evaluating robustness of machine learning models
- **[Towards Evaluating the Robustness of Neural Networks](https://arxiv.org/abs/1706.06083)** by Aleksander Madry et al.

---
