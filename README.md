# lme4_lmer_doublebar
Practical, reproducible demonstration of how to preserve meaningful contrast coding when simplifying random effects structures of lmer models with || .

## Motivation 

When fitting mixed-effects models with the `lmer()` function from the `lme4` package in R, it is common to simplify the random-effects structure in order to avoid overparameterization, singular fits, or non-convergence. One common approach is to replace the single bar (`|`) syntax with the double bar (`||`) syntax to remove correlations between random effects.

However, when factors are included in the random-effects structure, the use of `||` can unintentionally alter the underlying coding of the model matrix. In particular, contrast coding for categorical predictors may be lost, leading to parameterizations that differ from what users often expect. This issue is easy to overlook and can substantially affect the interpretation of the model. 

In this repository, I share a transparent and reproducible walkthrough of this issue and demonstrate practical solutions for preserving intended contrast coding when using double bar syntax models. Although the `lme4` documentation notes that the double bar syntax is intended for design matrices containing numeric predictors, it is common to see models specified with factors in the random-effects structure without awareness of how this affects contrast coding and parameterization. In practice, brief documentation notes can be easy to overlook when first learning a package or modeling framework. For this reason, I decided to share this demo, which I originally developed several years ago for the research lab I was working in, to provide a more explicit and reproducible walkthrough of the issue and its practical implications.

---

## Contents

This repository contains a script with examples that illustrate:

- the difference between single bar (`|`) and double bar (`||`) syntax in `lmer()` models
- differences between factor coding and manually specified indicator variables
- the difference between interaction syntax using `*` versus `:`
- practical strategies for preparing datasets for double bar syntax models
- an example for an informed model reduction workflow based on principal components analysis, while preserving interpretable parameterization

For reproducibility, the script is shared along with the dataset used in the user case example. The data come from a study that was published by colleagues: Huttenlauch, C., De Beer, C., Hanne, S., & Wartenburger, I. (2021). Production of prosodic cues in coordinate name sequences addressing varying interlocutors. *Laboratory Phonology*, 12(1). Data and code from this study are also shared on the Open Science Framework. 

---

## Intended Audience

This repository may be particularly useful for researchers and analysts who:
- use the `lme4` R package for mixed-effects modeling
- encounter convergence issues or singular fits
- simplify random-effects structures using `||`
- work with categorical predictors
- are somewhat familiar with contrast coding (otherwise, I can highly recommend the paper by Schad et al. listed below) 
- want to better understand how model syntax affects parameterization and interpretation

---

## References and Further Reading

This workflow is informed by documentation and literature on mixed-effects modeling, contrast coding, and random-effects specification. Relevant references and recommended reading materials are listed below.

- Bates, D., Mächler, M., Bolker, B., & Walker, S. (2015). Fitting linear mixed-effects models using lme4. *Journal of statistical software*, 67, 1-48.
- Schad, D. J., Vasishth, S., Hohenstein, S., & Kliegl, R. (2020). How to capitalize on a priori contrasts in linear (mixed) models: A tutorial. *Journal of memory and language*, 110, 104038.
- Official `lmer()` documentation:  
  [lmer() reference documentation](https://lme4.github.io/lme4/reference/lmer.html?utm_source=chatgpt.com)

---

## Notes

When I started working on this issue, I found relatively few accessible explanations demonstrating how contrast coding changes under double bar syntax models in practice. I hope the materials shared here are useful to others facing similar modeling challenges and provide a practical starting point for further exploration.

This repository presents one possible workflow for preparing data and specifying mixed-effects models. Depending on the modeling context, alternative valid approaches may also be appropriate.

Feedback and suggestions for improvement are welcome.
