---
layout: page
title: Computational capability buildout
description: Building a Drug Discovery Platform from Zero — and Making It Count
img: assets/img/glen-carrie-unsplash.jpg
importance: 2
category: systems and platforms
related_publications: false

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Image from link.
</div>


<h4>Context</h4>
<p>In an early-stage biotech environment, there was no computational infrastructure, no established workflows, and no prior computational hire. I was the first. The company had a scientific vision — applying machine learning to drug target discovery — but no platform to execute it on while needing to produce credible early results quickly.
The mandate was effectively two things at once: build the foundation, and immediately generate results credible enough to anchor a funding narrative.</p>


<h4>The Problem</h4>
<p>The core tension was speed versus rigour. Building a computational drug discovery platform properly takes time — defining the right architecture, validating analytical choices, ensuring results are reproducible and defensible. But the business needed a working proof-of-concept and a compelling investor story within months, not years. Underneath both sat a practical bottleneck: even if the ML platform generated promising drug target predictions, biologists needed to validate them experimentally — a process that, at the time, took three weeks per screen to analyse manually.</p>


<h4>What I Did</h4>
<p>The first task was infrastructure — defining requirements for compute, tooling, and analytical workflows from scratch, and architecting the AWS environment that would underpin all downstream work.
In parallel, I worked with the founders and biology team to define a more focused product angle — one grounded in where the company had genuine scientific and operational advantages — and translated that into a product vision and roadmap.
The third thread was the validation bottleneck. Automating the screening analysis pipeline compressed turnaround from three weeks to 30 minutes, turning a slow sequential handoff into a rapid feedback loop for the biology team. This wasn't a secondary project — it was what made the R&D loop viable. Speed and rigour were no longer in direct conflict.
Bridging the founders was the hardest stakeholder challenge throughout — keeping scientific credibility and commercial urgency in view simultaneously.</p>


<h4>The Outcome</h4>
<p>The platform POC generated credible results across multiple disease indications. The automated screening pipeline enabled the iterative R&D cadence the ML platform required.</p>


<h4>What This Illustrates</h4>
<p>This was simultaneously a platform build, a product strategy problem, and an R&D workflow design challenge — all running under significant time pressure. The work required identifying where the real bottlenecks were, maintaining a focused product angle under pressure, and keeping technical rigour and commercial urgency in tension without letting either collapse.</p>
