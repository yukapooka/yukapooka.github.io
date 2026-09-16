---
layout: page
title: Coffee Archive v1.0
description: A private coffee archive for capturing, organizing, and revisiting coffee experiences.
img: assets/img/coffee.png
category: coffee appreciation
related_publications: false

---
<h4>Overview</h4>
<p>coffee-archive-copilot turns scattered coffee notes into structured archive cards. Each entry can hold bean details, roaster notes, opening notes, what lingered, café or place context, collections, and interpretation fields.</p>

<p>The project is based on a simple idea:</p>
<ul>
    <li>Archive is infrastructure.</li>
    <li>Interpretation is the product.</li>
    <li>Learning is the outcome.</li>
</ul>

<p> Capture → Archive → Revisit → Interpret</p>

<p> V1.0 addresses the infrastructure layer by preserving the coffee experience first, then leaving room for interpretation to happen later.</p>
<br />

<h4>The Problem:</h4>
<p>Coffee experiences are surprisingly difficult to keep track of over time:</p>
<ul>
    <li>cafés don't always provide tasting slips or detailed coffee information</li>
    <li>notes end up scattered across photos, screenshots, notebooks, and messages</li>
    <li>individual coffees are easy to remember, but comparisons across many cups are difficult</li>
    <li>the more coffees you try, the harder it becomes to remember what you actually liked and why</li>
</ul>
<p>So the digital archive gives those experiences a consistent structure that can be searched and revisited later.</p>

---
<h4>What this App does:</h4>
<ul>
    <li>captures coffee experiences as structured archive cards</li>
    <li>records bean details, roaster notes, opening notes, and what lingered</li>
    <li>stores café, place, date, process, origin, and variety metadata</li>
    <li>supports entry creation, editing, and detail views</li>
    <li>organizes entries through collections</li>
    <li>displays collection chips on archive cards</li>
    <li>supports search, filtering, and sorting</li>
    <li>includes select mode and delete-selected workflow</li>
    <li>runs as a private deployed web app</li>
</ul>
<br />

---
<h4>Screenshots:</h4>
<h5>Archive Homepage</h5>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:80%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/coffee-archive-screenshot.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    Searchable archive homepage with filters, collection chips, and archive card count.
</div>
<br />

<h5>Entry Detail Page</h5>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:80%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/coffee-archive-edit-entry.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    Structured entry page for reviewing bean details, tasting notes, context, and collections.
</div>
<br />

<h5>Entry Entry Page</h5>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <div style="width:80%; margin:0 auto;">
            {% include figure.liquid loading="eager" path="assets/img/coffee-archive-edit-detail.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>
</div>
<div class="caption">
    Edit form for updating coffee notes, metadata, collections, and interpretation fields.
</div>
<br />

---
<h4>Future Work</h4>
<p>Planned improvements include:</p>
<ul>
    <li>Build v2.0 will add a media layer and tagging workflow.</li>
    <li>Build v3.0 will add an interpretation layer on top of the archive.</li>
</ul>
<br />
---
<h4>Current Tech Stack</h4>:
<p>Built with AI-assisted development using Codex, with a Next.js / TypeScript frontend and PostgreSQL backend accessed through Prisma 7 and the PrismaPg adapter.</p>
<ul>
    <li>Frontend: Next.js, TypeScript, Tailwind CSS</li>
    <li>Backend / data: PostgreSQL + Prisma 7</li>
    <li>Deployment: Vercel</li>
    <li>Access: private web app protected by username/password authentication</li>
    <li>Development: AI-assisted coding workflow with Codex</li>
</ul>
<br />

<div style="border-left: 4px solid #007acc; padding-left: 15px; margin: 10px 0;">
    The archive is designed to be used wherever the coffee experience happens. The responsive interface works across desktop and mobile, allowing entries to be created, edited, or deleted from a phone as well as a computer.
</div>

---
<h4>Links</h4>
<h5>GitHub Repository</h5>
<p>Explore the source code, system architecture and implementation details:</p>

<p><a href="https://github.com/yukapooka/coffee-archive-copilot">View Repository -> </a></p>
<br />