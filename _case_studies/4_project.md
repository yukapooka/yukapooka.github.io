---
layout: page
title: Decision Design Across the Oncology Care Pathway
description: Examined how diagnostic and monitoring systems influence interpretation, trust, and action across high-stakes oncology workflows.
img: assets/img/12.jpg
importance: 4
category: decision systems
related_publications: false

---

<h4>Context</h4>
<p>In high-stakes oncology workflows, clinical decisions — whether to change a treatment, flag a recurrence risk, or continue monitoring — increasingly rely on outputs from computational diagnostic pipelines. These systems are powerful, but they surface a consistent and underappreciated problem: the gap between what a system reports and what a clinician can reliably interpret. This case study examines work done during the product development of an oncology monitoring pipeline, focused on understanding how data quality, algorithmic sensitivity, and output design collectively shape clinical interpretation — and where that process breaks down.</p>


<h4>The Problem</h4>
<p>The core issue wasn't model performance in isolation — it was how outputs were being used in practice, and the conditions under which those outputs were generated. Oncology diagnostics operate in a fundamentally constrained data environment. Patient samples are difficult to acquire, often limited in volume, and frequently of non-optimal quality — degraded, contaminated, or collected under conditions that fall outside what a pipeline was originally designed to handle. This is not an edge case. It is the norm. And it creates a compounding challenge: an algorithm must be sensitive enough to detect meaningful signals in imperfect material, while remaining accurate enough that clinicians can trust what it returns. When that balance isn't right — or when it isn't clearly communicated — the consequences ripple outward. Clinicians were making consequential decisions based on single signals from a pipeline whose outputs were subject to a range of interacting variables: real-world sample variability, analytical sensitivity constraints and input quality limitations. Each of these introduced uncertainty that wasn't always visible in the final reported result. The risk wasn't that the system was wrong. It was that the system's limitations weren't legible at the point of interpretation — and in a clinical setting where a result might inform a treatment change or a recurrence assessment, that invisibility had real consequences. Data quality is not just a technical upstream problem. It is a product problem, because it directly determines whether the outputs a clinician receives are ones they can act on with confidence.</p>


<h4>What I Did</h4>
<p>As part of the product development process, I investigated how experimental variables interacted with pipeline outputs and where interpretation was most likely to go wrong. This involved:

Mapping the full range of conditions that could affect output quality — from upstream sample handling and collection variability to downstream analytical thresholds — to understand where the pipeline was most sensitive to real-world input degradation Designing and running stress-tests across edge cases and boundary conditions, including deliberately non-optimal sample inputs, to identify where the pipeline produced results that were technically valid but potentially misleading in clinical context Working across cross-functional stakeholders to define interpretation thresholds that balanced sensitivity and accuracy in a way that reflected real operating conditions — not idealised ones — and that would hold up when samples were, as they often are, imperfect Translating findings into product documentation that made the system's constraints explicit and actionable at the point of use, so clinicians had a clearer framework for contextualising results rather than treating outputs as unconditional ground truth

The underlying design question throughout was not just "does this algorithm perform well?" but "under what conditions can a clinician trust what this returns — and does the product make those conditions clear?"</p>



<h4>The Outcome</h4>
<p>The work resulted in updated product documentation that formally incorporated interpretation constraints, making previously implicit limitations visible to clinical users. Threshold definitions were refined to better reflect real-world operating conditions, including the variability introduced by suboptimal sample quality. The result was a more honest product — one whose outputs were calibrated to the conditions clinicians actually encounter, not the conditions that make performance benchmarks look cleanest.</p>


<h4>What This Illustrates</h4>
<p>Diagnostic systems don't fail only when the model is wrong. They fail when data quality constraints aren't surfaced, when sensitivity and accuracy tradeoffs aren't made explicit, and when workflow design leaves clinicians without the context they need to interpret uncertainty well. In oncology, where samples are scarce and decisions are consequential, building a product that performs reliably means designing for the messiness of real clinical data — not around it. That principle has shaped how I think about product work in high-stakes environments ever since: technical performance and decision quality are related but not the same thing, and closing the gap between them is a product problem worth solving.</p>
