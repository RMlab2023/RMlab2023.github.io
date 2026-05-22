---
layout: post
title: "Six QC lessons from our first CRUK SI XT workflows"
date: 2026-05-22
author: Ralitsa Madsen
categories: [science, open-science]
excerpt: >
  Mass cytometry is powerful because it multiplexes biology — but that same
  multiplexing makes invisible technical confounders easy to mistake for
  biological signal. Six quality-control lessons from the Madsen Lab's first
  CyTOF XT workflows, shared in the spirit of collaboration.
---

Mass cytometry is powerful because it multiplexes biology, but that same multiplexing makes invisible technical confounders easy to mistake for biological signal. In this blogpost, I will walk you through some recent lessons of our own — so you do not get fooled by your own or anybody else's data!

It has been more than two months since we got our XT instrument installed at the CRUK Scotland Institute, thanks to generous funding from the UKRI FLF programme. Since then, we have been busy QC'ing existing and new panels. Why? Because with the privilege of having our own instrument, and having access to it all the time, comes responsibility: responsibility for developing internal standards and robust expectations for experimental design and result interpretation.

Having now finished the analyses of our initial QC, there are a few lessons that I thought would be useful to share with the wider community. These are not universal rules, but QC principles that emerged from our first XT workflows. I share them in the spirit of collaboration. They are for people generating data, and for those evaluating datasets as reviewers, editors, collaborators or future data re-users.

I know that time is limited for everyone these days, so I shall keep this in a bite-sized format, supported by actual data from a recent presentation I gave at UMons, thanks to Standard BioTools. There are six key bites, with the take-home messages also captured visually in the following scribble. Thanks ChatGPT!

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig1-overview-information-distortion-control.png" alt="Hand-drawn summary: information (what biology we capture), distortion (what can mislead us) and control (how we ensure trustworthy inference).">
  <figcaption>Information, distortion and control — a visual summary of the six QC lessons, and the goal of turning high-dimensional measurement into quantitative biological insight.</figcaption>
</figure>

## 1) Do not validate signalling antibodies without signalling biology

Understand the biology of what you are measuring, and let that biology shape your experimental validation.

If you are validating a signalling antibody, you need more than a positive-looking signal. You need a signal-inducing perturbation, measurements that cover the relevant time scale of the signalling event, targeted inhibitors or genetic controls to assess antibody specificity, and knowledge of the cell states or cell types that are actually permissive to the signalling event in question.

In other words: a signalling antibody should be tested in a context where the signal is expected to change, at a time point when the pathway should respond, and in cells where the pathway is competent to respond.

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig2-antibody-validation-stimulus-time.png" alt="pAKT Ser473 and pS6 Ser240/244 single-cell distributions across stimuli, time points and PIK3CA genotypes.">
  <figcaption>Validating PTM-specific antibodies with signalling biology: pAKT Ser473 and pS6 Ser240/244 responses across stimuli (H₂O, IGF1, EGF), time points (5–30 min) and PIK3CA genotypes (WT, 1×H1047R, 2×H1047R), with BYL719 (alpelisib) as a pathway-inhibitor control.</figcaption>
</figure>

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig3-antibody-validation-cell-state.png" alt="pS6 Ser240/244 responses to IGF1 over time in cycling versus non-cycling cells.">
  <figcaption>Cell state matters: pS6 Ser240/244 (an mTORC1 activity marker) responds to IGF1 over time in cycling (pRB-positive, non-apoptotic) cells, but is essentially flat in non-cycling (pRB-negative) cells.</figcaption>
</figure>

## 2) Do not mistake abundance for antibody performance

The ability to measure large differences in antigen abundance may be confounded by suboptimal antibody performance.

A low-sensitivity antibody can appear to perform well when the target is abundant, but fail when the target in a sample is close to the limit of detection. This is especially important because an antibody can be specific and still not be sensitive enough for a particular biological context, fixation condition, dissociation workflow or sample preparation.

In the example below, two different pERK T202/Y204 antibodies give similar distributions in an iPSC sample that had not suffered antigen leakage. At first glance, both antibodies look acceptable. However, in the more challenging setting of fixed venous-like endothelial spheroids subjected to dissociation, the picture is very different. We now clearly unmask a substantially lower sensitivity for one of the two antibodies.

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig4-antibody-sensitivity-abundance.png" alt="Two pERK antibodies compared in venous-like endothelial cells and iPSCs.">
  <figcaption>Antibody sensitivity × antigen abundance: two pERK T202/Y204 antibodies (167Er, BD vs 171Yb, Standard BioTools/CST) compared in venous-like endothelial cells (VLEC; MUT and WT) and iPSCs. The antibodies look comparable in the high-antigen iPSCs but diverge where antigen levels are low.</figcaption>
</figure>

The lesson is simple: do not assume that antibody performance observed in an easy sample will hold in a harder one. Test antibodies under conditions that resemble the actual samples you care about.

## 3) Do not overinterpret distributions from n < 500 cells

The previous example was not the only plot twist.

The more sensitive pERK antibody gave rise to a very different single-cell distribution in an otherwise identical sample, with one important exception: the number of target cells was lower, with fewer than 500 endothelial cells after debarcoding and gating.

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig5-cell-number-distribution.png" alt="The same antibodies in a well-sampled sample versus a sparsely sampled one.">
  <figcaption>The same antibodies in a well-sampled sample (Sample 2; n = 815 MUT / 693 WT) versus a sparsely sampled one (Sample 3; n = 241 MUT / 210 WT endothelial cells). With fewer than 500 cells per group, the recovered distributions become noticeably less stable.</figcaption>
</figure>

This got us thinking. How many target cells do we need after debarcoding and gating to recover a stable approximation of the underlying single-cell distribution?

The simulation below holds the answer. Based on this analysis, we now treat n > 500 as a practical lower bound, and n > 750 as preferable, for robust distribution-level inferences in this type of analysis. Anything lower can result in substantial sampling variability, especially if the biological question depends on the shape of the distribution rather than just a simple average.

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig6-bootstrap-cell-number-simulation.png" alt="Bootstrap convergence of the KS statistic versus subsample size for iPSCs.">
  <figcaption>How many cells are enough? Bootstrap convergence of the Kolmogorov–Smirnov (KS) statistic versus subsample size (iPSCs; reference n = 8,365). Distributions stabilise as cell number grows; the red dashed line marks a panel with only 408 cells. We aim for n > 750 for robust convergence.</figcaption>
</figure>

Of course, this is not a universal threshold for every marker, cell type or biological question. Rare subpopulations, skewed distributions, subtle treatment effects and clustering-based analyses may require more cells. But the general principle is important: if the target population is too small, the distribution you see may be as much a sampling artefact as a biological feature.

## 4) Do not ignore isotope impurity

Mass cytometry relies on rare earth metal-conjugated antibodies. These metals are not 100% pure. Each metal has characteristic impurity percentages into neighbouring mass channels of the same element, and occasionally into adjacent elements. These values are available from the published isotope purity matrix.

This matters because isotope impurities can become significant confounders when a high-signal antigen is detected through a metal with substantial impurity into another channel.

In the example below, 168Er constitutes approximately 3.2% of 167Er. In practical terms, this means that approximately 3.2% of one of my pERK antibodies is actually tagged with 168Er rather than 167Er. If the pERK signal is very high, then this 3.2% contribution becomes significant in absolute terms. It can then contribute to the apparent detection of an unrelated marker, if that marker is detected with an 168Er-conjugated antibody.

In the example, pSMAD2/3 is detected with 168Er in two different panels: one that contains a 167Er-conjugated pERK antibody, and one that does not. There is clear evidence of spillover. In this case, the issue was both predictable from the isotope purity matrix and visible in the data, so our decision was simple: avoid this combination altogether in the final panel.

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig7-isotope-impurity-spillover.png" alt="pSMAD2/3 (168Er) distributions stratified by pERK (167Er) intensity, showing a right-shift in the pERK-high fraction.">
  <figcaption>Isotope-impurity spillover check: pSMAD2/3 (168Er) stratified by pERK (167Er) intensity across treatments and genotypes. The right-shift in the "pERK high" fraction, relative to the dashed green reference panel that lacks a 167Er neighbour, reveals impurity contamination.</figcaption>
</figure>

The lesson is that predictable impurity risks should be considered during panel design, especially when high-signal donor channels sit next to lower-signal recipient channels.

## 5) Do not rescue bad panel design with computational correction if you can avoid the problem upfront

Beyond isotope impurities, you also need to be careful of oxides. Some elements are more oxide-prone than others. 150Nd is one example. It can give rise to a derivative that is +16 Da heavier, meaning that it is detectable in the 166 mass channel.

In one of our panels, we had 150Nd tagged onto an antibody used for SOX2 detection. SOX2 is highly abundant in iPSCs, so we worried that it might confound our measurements of total AKT through a 166Er-conjugated antibody. This would be especially concerning if the total AKT signal were low, either because of intrinsic protein abundance or because of low antibody sensitivity.

How can we check this? Easily. Plot the total AKT signal against the expected contaminating counts contributed by the 150Nd donor channel. This can be calculated for different oxide fractions, up to the established maximum of 2.1%.

As you can see in the following plot, anything that falls close to, or on, the red lines may be significantly confounded by oxide formation.

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig8-oxide-checks-akt.png" alt="Total AKT versus the 150Nd donor signal with theoretical oxide lines.">
  <figcaption>Oxide check: total AKT (166Er) plotted against the 150Nd (SOX2) donor signal, with theoretical oxide lines. Points near or above the red lines (≤ 2.1% oxide) may be confounded by oxide formation; higher donor signal lets the oxide dominate a larger fraction of the AKT channel.</figcaption>
</figure>

To sum up: be aware of oxide formation, and avoid placing low-abundance or low-signal targets in channels that may suffer from oxide spillover. Rather than attempting computational correction after the fact, avoid the problematic combination entirely where possible.

## 6) Do not trust correlations before estimating the technical floor

We all know that correlation is not causation. But when is a correlation worth noticing in the first place?

It is well known from proteomics that cell size and total protein content can drive variation across many measured proteins. Bigger cells, or cells with higher total protein content, tend to produce higher signal across many channels, including background. This means that correlations between measured markers are often expected to be positive, even when there is no meaningful biological relationship between those markers.

The same applies to mass cytometry if you have no way of correcting for cell size or total protein content. In other words, a positive correlation may be worthless.

How would you know?

Our tip is to include at least one negative marker in all panels. By negative marker, I mean one or more antibodies that should only give rise to background staining, either because they do not work in that context or because their antigen is not present in your sample. You can then calculate the correlation between these negative markers and all other markers to establish a technical correlation floor.

As shown below, the 95th percentile of this technical correlation floor can vary depending on the stickiness of your samples. This means it is important to estimate it empirically for each sample preparation. Otherwise, you risk mistaking generic sample-wide variation for coordinated pathway activity, signalling rewiring or meaningful cell-state biology.

<figure>
  <img src="/assets/images/posts/2026-05-22-six-qc-lessons/fig9-spurious-correlations-floor.png" alt="Distribution of background Spearman correlations for non-staining markers in iPSCs versus spheroids.">
  <figcaption>Estimating the technical correlation floor: the distribution of background Spearman correlations (non-staining markers versus all others). The 95th percentile differs between iPSCs (0.8) and spheroids (0.46), so it must be estimated empirically for each sample preparation.</figcaption>
</figure>

## Bottom line

In highly multiplexed single-cell signalling assays, rigour is not demonstrated by the number of markers measured. It is demonstrated by showing that each signal is biologically plausible, technically detectable, sufficiently sampled and protected from predictable channel-level artefacts.

This is not a nice-to-have. It is a must-have, especially as AI-driven models increasingly ingest datasets without access to the experimental execution details, tacit domain knowledge or unpublished QC standards needed to interpret them properly.

*Acknowledgement: Initial draft written by Dr Ralitsa Madsen. ChatGPT 5.5 / Claude Opus 4.7 were used for type-setting, typo corrections and textual clarifications. The final content was reviewed and edited by the author.*
