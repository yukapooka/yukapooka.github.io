---
layout: page
title: Decision Design Across the Oncology Care Pathway
description: Examined how diagnostic and monitoring systems influence interpretation, trust, and action across high-stakes oncology workflows.
img: assets/img/oncology_decision.jpg
importance: 4
category: decision systems
related_publications: false

---

<h4>Context</h4>
<p>In high-stakes oncology workflows, clinical decisions — whether to adjust a treatment, flag a recurrence risk, or continue monitoring — increasingly rely on outputs from computational diagnostic pipelines. These systems are useful, but they surface a consistent challenge: the gap between what a system reports and what a clinician can reliably act on.</p>


<h4>The Problem</h4>
<p>The core issue wasn't model performance in isolation — it was how outputs were being used in practice, and under what conditions they were generated. Oncology diagnostics operate in a constrained data environment. Patient samples are difficult to acquire, often limited in volume, and frequently of non-optimal quality. This is not an edge case — it is the norm. An algorithm needs to be sensitive enough to detect meaningful signals in imperfect material, while remaining accurate enough that clinicians can trust what it returns. Data quality is not just an upstream technical problem — it directly determines whether outputs are ones a clinician can act on with confidence.</p>


<h4>What I Did</h4>
<p>As part of the product development process, I investigated how experimental variables interacted with pipeline outputs and where interpretation was most likely to go wrong. This involved mapping the conditions that could affect output quality, running stress-tests across edge cases and non-optimal sample inputs, and working with cross-functional stakeholders to define interpretation thresholds that reflected real operating conditions rather than idealised ones. Findings were translated into product documentation that made the system's constraints explicit and usable at the point of clinical decision-making.</p>



<h4>The Outcome</h4>
<p>The work resulted in updated product documentation that made interpretation constraints visible and actionable at the point of use. Thresholds were refined to better reflect the real conditions clinicians work with — including the variability that comes with imperfect sample quality — giving them a clearer and more honest basis for contextualising pipeline outputs.</p>


<h4>What This Illustrates</h4>
<p>Diagnostic systems can fall short not because the model is wrong, but because the conditions under which outputs can be trusted aren't made clear. In settings where samples are limited and decisions are consequential, designing for real-world data variability — rather than around it — is part of what makes a product genuinely useful. Technical performance and decision quality are related, but they're not the same thing, and the gap between them is worth designing for explicitly.</p>
