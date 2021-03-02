---

layout: post
author: yuka
title: Tumor Heterogeneity in Asian cancers
description: Understanding how tumors evolve
categories: [Genomics, Oncology ]
image: https://source.unsplash.com/3vycqsMutjE/1600x1200 

---
<div align="center"><small>Photo by  <a href = "https://unsplash.com/photos/hNrd99q5peI">Paweł Czerwiński </a> on Unsplash</small></div>

## Short Summary
This was my first PhD project where I studied the mutations in 4 colorectal cancer patients to understand the aggressiveness of their disease. I analyzed the targeted sequencing datasets of 24 biopsy samples taken from different parts of the tumors, identified DNA mutations and constructed phylogeny trees to understand how the patient's tumors have evolved. I also performed statistical analyses to highlight genes that are mutated and exhibit correlated changes in their gene activities using gene expression datasets profiled from the same samples.

This study was published in the Molecular Oncology journal:

<p><b><a href="https://febs.onlinelibrary.wiley.com/doi/full/10.1002/1878-0261.12012">"Multiregion ultra‐deep sequencing reveals early intermixing and variable levels of intratumoral heterogeneity in colorectal cancer. "Molecular Oncology, 11(2):124-139 (2016)</a></b><br />
Y.Suzuki, ..., I.B.Tan.</p>

---
## Problem
Heterogeneity of genetic mutations in different parts of the tumor can explain why cancer treatments fail as diagnosis is based on focusing on one section of the tumor tissue.  This leads to treatment failure, drug resistance and metastasis in some cases. 

---
## Approach
I used deep next-generation DNA sequencing to sequence the regions of 799 known cancer genes in each section of the tumor biopies taken from 4 patients. 'Deep sequencing' is needed so that my analysis can capture rarer genetic mutations that could lead to relapse if they were not identified and eradicated by treatment. 



Computed all pairwise correlations of gene copy number changes with gene expression values of the same gene (799 genes in total) from the same sample: Findings revealed genes that might have decreased or increased number of gene copies or gene expression, which could affect the growth of cancer cells.


---
## Outcomes of the Project
Ultra‐deep sequencing dramatically improved the precision of the analyses of tumor heterogeneity within the same tissue. The different degree of heterogeneity acros different patients demonstrates that every tumor is unique on its own and that treatment decisions should be tailored to the profile of the patient. My analysis also identified some interesting genes that can serve as biomarkers for tracking or monitoring the patient's progress during treatment.
---


<div align="center">
  <img class="featured-image img-fluid" src="{{ site.baseurl }}/assets/images/ith-pt1.001.png" alt="{{ page.title }}">
</div>
