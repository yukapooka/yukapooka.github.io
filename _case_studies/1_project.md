---
layout: page
title: Internal analytics platform
description: From Fragmented Scripts to a Shared Platform: Building an Internal Analytics System for Sequencing R&D
img: assets/img/12.jpg
importance: 1
category: systems and platforms
related_publications: true

---

<h4>Context</h4>
<p>At Illumina, sequencing R&D teams relied on a patchwork of individual scripts and ad hoc workflows to evaluate platform performance. There was no shared system, no consistent methodology, and no way for teams to build on each other's work. Every analysis started from scratch.</p>


<h4>The Problem</h4>
<p>The fragmentation wasn't just inefficient — it created interpretation risk. When different scientists used different methods on the same data, results weren't comparable. Leadership couldn't trust aggregate performance signals, and time-to-insight was slow enough to create bottlenecks in platform development cycles.</p>


<h4>What I Did</h4>
<p>I led the end-to-end definition and delivery of a cloud-based analytics platform to standardise how R&D teams evaluated sequencing performance. Specifically:</p>

<ul style="padding-left: 30px;">
    <li>Ran structured requirements-gathering sessions with cross-functional scientific stakeholders to surface what a shared platform actually needed to do</li>
    <li>Authored full product specifications in Confluence, with LucidChart process diagrams to make workflows legible across technical and non-technical audiences</li>
    <li>Managed the JIRA backlog and ran weekly delivery syncs with the software engineering team to keep scope clear and progress visible</li>
    <li>Mentored 8 scientists across Singapore and the US on the new workflows and reusable code practices so adoption wasn't dependent on me as a bottleneck</li>
</ul>


<h4>The Outcome</h4>
<p>Reduced time-to-insight by 70%. 
Scientists could access consistent, reproducible analytics without starting from zero each time. Platform performance reporting to product and scientific leadership became a weekly cadence rather than an occasional exercise.</p>


<h4>What This Illustrates</h4>
<p>This wasn't purely a technical build — it was a product problem. The core challenge was that fragmentation had been normalised, so part of the work was reframing a workflow inefficiency as a platform risk worth solving. Once that framing landed with stakeholders, the delivery followed.</p>







Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

To give your project a background in the portfolio page, just add the img tag to the front matter like so:

    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
