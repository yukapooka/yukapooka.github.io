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
<p>When I joined Engine Biosciences, there was no computational infrastructure, no established workflows, and no prior computational hire. I was the first. The company had a scientific vision — applying machine learning to drug target discovery — but no platform to execute it on, and an active fundraising clock running in the background.
The mandate was effectively two things at once: build the foundation, and immediately generate results credible enough to anchor a funding narrative.</p>


<h4>The Problem</h4>
<p>The core tension was speed versus rigour. Building a computational drug discovery platform properly takes time — defining the right architecture, validating analytical choices, ensuring results are reproducible and defensible. But the business needed a working proof-of-concept, positive results, and a compelling investor story within months, not years.
There was also a strategic question that hadn't been fully resolved: in a crowded drug discovery landscape dominated by well-capitalised Western competitors, what was Engine's actual edge?
And underneath both of these sat a practical bottleneck that threatened to slow everything down: even if the ML platform generated promising drug target predictions, biologists needed to validate them experimentally through CRISPR genetic screening — a process that, at the time, took three weeks per screen to analyse manually.</p>


<h4>What I Did</h4>
<p>The first task was infrastructure — defining requirements for compute, tooling, and analytical workflows from scratch, and architecting the AWS environment that would underpin all downstream work.
In parallel, I worked with the founders and biology team to answer a harder strategic question: given the competitive landscape, where did Engine have a genuinely defensible advantage? I worked to identify a more focused product angle — grounded in the specific disease areas and clinical networks where Engine had real access — and translated that into a sharper product vision and scientific roadmap that could hold up to investor scrutiny.
The third thread was a validation bottleneck that threatened to slow everything down. The ML platform and the experimental screening pipeline were part of the same iterative cycle — predictions needed to be validated, and results needed to feed back into the model. At three weeks per screen, that cycle was too slow for the pace the business required. Automating the screening analysis pipeline compressed this from three weeks to 30 minutes, turning what had been a sequential handoff into a rapid, self-serve feedback loop for the biology team.
This wasn't a secondary project — it was what made the R&D loop viable. Speed and rigour were no longer in direct conflict.
Bridging the founders remained the hardest stakeholder challenge throughout — keeping scientific credibility and commercial urgency in view simultaneously, and structuring the work so that results were both defensible and narratively compelling for investors.</p>


<h4>The Outcome</h4>
<p>The platform POC generated credible results across multiple disease indications, with a differentiated product angle that was difficult for larger competitors to replicate. The automated screening pipeline compressed the validation cycle from weeks to hours, enabling the iterative R&D cadence the ML platform required to generate results at the pace the business needed. The programme became the primary vehicle for fundraising, contributing directly to <b>USD $7M in venture funding within 18 months</b>.</p>


<h4>What This Illustrates</h4>
<p>This was simultaneously a platform build, a product strategy problem, and an R&D workflow design challenge — all running under significant time pressure. The work required identifying where the real bottlenecks were, finding the strategic angle that turned the platform's constraints into a focused advantage, and keeping technical rigour and commercial urgency in tension without letting either collapse.</p>
