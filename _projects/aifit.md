---
layout: page
title: AIFit
description: A human-in-the-loop product decision tool for evaluating whether an AI feature should be built, narrowed, prototyped, or avoided.
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

<p>I built AIFit to explore a more systematic approach to evaluating new AI product features.</p>
<br />

---
<h4>The Solution - AIFit</h4>
<p>AIFit combines structured feature inputs, risk-specific guidance, and LLM evaluation to generate a decision-support tool.</p>
<p>The goal is not to automate product decisions, but to help teams ask better questions before committing resources.</p>
<br />

---
<h4>System Architecture</h4>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:70%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/AIFit_System_Flow.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    AIFit transforms an AI feature idea into a risk-aware decision-support report through structured evaluation, risk-specific guidance, and human review planning.
</div>
<br />

---
<h4>Key Design Decisions</h4>
<h5>(i) Risk-specific Evaluation</h5>
<p>AIFit identifies a dominant risk type and adapts review and validation guidance accordingly. </p>
Examples of risk types include:
<ul>
    <li>False Validation</li>
    <li>Emotional Vulnerability</li>
    <li>Financial Manipulation</li>
    <li>Fairness / Bias</li>
    <li>Privacy / Data Sensitivity</li>
</ul>    
<br />
<h5>(ii) Structured outputs instead of free-form advice</h5>
<p>AIFit breaks the evaluation into specific fields such as risk type, risk themes, review package, validation method, metrics, move-forward criteria, and stop/redesign signals. This makes the output easier to inspect, compare, and challenge.</p>
<br />
<h5>(iii) Human-in-the-loop By Default</h5>
<p>The tool generates recommendations, but all outputs are framed as decision support rather than automated decisions. Product, domain, legal, policy, or compliance experts remain responsible for reviewing outputs before launch decisions.</p>
<br />
<h5>(iv) Explainable Outputs</h5>
<p>AIFit provides:</p>
<ul>
    <li><b>Risk classification</b> – Identifies the dominant product risk that should guide evaluation and governance.</li>
    <li><b>Risk themes</b> – Highlights the specific failure modes or concerns associated with the feature.</li>
    <li><b>Risk rationale</b> – Explains why the feature was assigned a particular risk classification.</li>
    <li><b>Review workflows</b> – Recommends who should review the feature, what artifacts to inspect, and when review should occur.</li>
    <li><b>Validation workflows</b> – Suggests how the feature should be tested, what scenarios should be covered, and what evidence is needed before launch.</li>
</ul>
<br />

<p>Together, these outputs make AIFit recommendations easier to interpret, review, and challenge.</p>
<br />

---
<h4>Example Outputs</h4>
<h5>Evaluation Summary Output</h5>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:80%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/evaluation_summary.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    AIFit generates a recommendation, Build Readiness score, risk classification, and rationale.
</div>
<br />

<h5>Build Boundaries Output</h5>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:80%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/what_to_build_not_build.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    AIFit separates useful product scope from risky implementation patterns.
</div>
<br />

<h5>Human Review Workflow Output</h5>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:80%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/human_review_workflow.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    AIFit specifies who should review the AI output, what artifacts to inspect, and what authority reviewers have.
</div>
<br />

<h5>Validation Workflow Output</h5>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:80%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/validation_workflow.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    AIFit helps teams define how the feature should be tested, what scenarios to include, what metrics to track, and when to move forward or redesign.
</div>
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
<p>Planned improvements include:</p>
<ul>
    <li><b>Separating risk classification from evaluation generation</b> – Improve explainability and make risk assignment easier to debug and validate independently.</li>
    <li><b>Externalizing the risk guidance library</b> – Move risk-specific guidance out of the prompt and into configurable files to simplify maintenance and future expansion.</li>
    <li><b>Support for additional risk categories</b> – Expand the framework as new recurring risk patterns emerge during testing and real-world usage.</li>
    <li><b>Prompt regression testing</b> – Evaluate prompt changes against a library of representative use cases to detect improvements or unintended degradations in output quality.</li>
    <li><b>Improved explainability for scoring</b> – Provide clearer reasoning for how AI Fit, Commercial Upside, Risk Burden, and Evidence Readiness scores are determined.</li>
    <li><b>Model comparison and evaluation</b> – Compare outputs across different LLMs to assess consistency, reasoning quality, and recommendation robustness.</li>
</ul>
<br />

---
<h4>Tech Stack</h4>
<ul>
    <li>Python</li>
    <li>Streamlit</li>
    <li>OpenRouter</li>
    <li>GitHub</li>
    <li>Streamlit Community Cloud</li>
</ul>
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

<h5>GitHub Repository</h5>
<p>Explore the source code, system architecture and implementation details:</p>

<p><a href="https://github.com/yukapooka/ai-fit">View Repository -> </a></p>
<br />