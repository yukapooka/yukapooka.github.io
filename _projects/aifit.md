---
layout: page
title: AIFit
description: A human-in-the-loop product decision tool for evaluating whether an AI feature should be built, narrowed, prototyped or avoided.
img: assets/img/aifit.png
related_publications: false

---
<h4>Overview</h4>
<p>AIFit helps product teams evaluate AI feature ideas across four dimensions:</p>
<ul>
    <li>AI Fit</li>
    <li>Commercial Upside</li>
    <li>Risk Burden</li>
    <li>Evidence Readiness</li>
</ul>

<p>The tool generates structured recommendations, human review workflows, and validation plans to support responsible AI product decisions.</p>
<br />

---
<h4>The Problem</h4>
<p>Many AI product discussions focus on capability and feasibility:</p>
<ul>
    <li>Can the model do it?</li>
    <li>Is the technology available?</li>
    <li>How quickly can we ship it?</li>
</ul>

<p>Less attention is often given to:</p>
<ul>
    <li>whether AI is the right solution;</li>
    <li>how the feature may influence human decisions;</li>
    <li>what risks should be reviewed before launch;</li>
    <li>how the feature should be validated.</li>
</ul>

<p>I build AIFit to explore a more systematic approach to evaluating new AI product features.</p>
<br />

---
<h4>The Solution - AIFit</h4>
<p>AIFit combines structured feature inputs, risk-specific guidance, and LLM evaluation to generate a decision support tool.</p>

<p>The goal is not to automate product decisions, but to help teams ask better questions before committing resources.</p>
<br />

---
<h4>System Architecture</h4>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/AIFit_System_Flow.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    AIFit transforms an AI feature idea into a risk-aware decision-support report through structured evaluation, risk-specific guidance, and human review planning.
</div>
<br />

---
<h4>Key Design Decisions</h4>
<h5>Risk-specific Evaluation</h5>
AIFit identifies a dominant risk type and adpats review and validation guidance accordingly.

Examples of risk types include:
<ul>
    <li>False Validation</li>
    <li>Emotional Vulnerability</li>
    <li>Financial Manipulation</li>
    <li>Fairness / Bias</li>
    <li>Privacy / Data Sensitivity</li>
</ul>    

<h5>Human-in-the-loop By Default</h5>
The tool generates recommendations, but all outputs are framed as decision support rather than automated decisions.

<h5>Explainable Outputs</h5>
AIFit provides:
<ul>
    <li>Risk Classification</li>
    <li>Risk Themes</li>
    <li>Risk Rationale</li>
    <li>Review Workflows</li>
    <li>Validation Workflows</li>
</ul>
<p>to make recommendations easier to interpret and challenge.</p>
<br />

---
<h4>Example Outputs</h4>
<h5>Evaluation Summary Output</h5>

<h5>Build Boundaries Output</h5>

<h5>Human Review Workflow Output</h5>

<h5>Validation Workflow Output</h5>
<br />

---
<h4>Lessons Learned</h4>
<p>Building AIFit reinforced several key ideas:</p>
<ul>
    <li>Prompt design is product architecture.</li>
    <li>Risk evaluation requires domain-specific guidance.</li>
    <li>Human review and validation are product features, not compliance afterthoughts.</li>
    <li>Explainability is often more valuable than additional model complexity.</li>
</ul>
<br />

---
<h4>Future Work</h4>
<br />

---
<h4>Tech Stack</h4>
<br />

---
<h4>Links</h4>
<h5>Live Demo</h5>
<p>Try AIFit using:</p>
<ul>
    <li>built-in example use cases, or</li>
    <li>your own AI feature idea through the custom evaluation workflow</li>
</ul>

<p><a href="https://www.linkedin.com/in/suzukiyuka/">Launch AIFit -> </a></p>

<h5>Github Repository</h5>
<p>Explore the source code, system architecture and implementation details:</p>

<p><a href="https://github.com/yukapooka/ai-fit">View Repository -> </a></p>
<br />