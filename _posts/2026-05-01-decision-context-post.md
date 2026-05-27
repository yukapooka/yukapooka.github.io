---
layout: post
title: The Hard Part of AI Products Is Not the Model. It Is the Decision Context
date: 2026-05-01
#tags: responsible_ai
categories: ai_products responsible_ai trust product_thinking
giscus_comments: false
related_posts: false

---

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/decision-article3.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    AI products are often discussed as if they were simply better software. But once outputs influence human judgment under uncertainty, product thinking must account for trust, misuse, override, and the uneven consequences of error.
</div>
<br />

---


### Opening Tension
<p>AI product discussions often begin with the model: accuracy, latency, benchmark scores, and feature quality. But in practice, the harder problem is often the decision context: what decision the system supports, who acts on the output, and what happens when it is wrong. Two related failures are common: optimizing the wrong proxy within the right environment, or placing a capable system into a decision environment it was never designed to serve. Both can produce technically functional products that fail in practice (Afroogh et al., 2024).</p>

<p>Two examples make this visible. Facebook’s News Feed algorithm illustrates the first failure mode: optimizing for engagement in a context where engagement is a poor proxy for the broader decision the product shapes. The INFANT trial illustrates the second: a detection system that performed its stated task correctly but did not improve outcomes because signal detection and clinical intervention are different decisions (INFANT Collaborative Group, 2017).</p>
<br />

---

### A model is not a decision
<p>One of the most common mistakes in AI product thinking is to treat model output as if it were the decision itself. In practice, output is only one part of a larger workflow. Users bring domain knowledge, constraints, incentives, and accountability into the process, and those factors shape whether AI becomes useful or harmful (Afroogh et al., 2024).</p>

<p>Facebook’s News Feed is a useful example, though it requires some care. Engagement is measurable and easy to optimize, but it is only a proxy for a more consequential question: what information people see, act on, and form views from. The empirical evidence on whether ranking amplifies misinformation and polarization remains mixed, with experimental and theoretical work pointing in somewhat different directions (Guess et al., 2023; Germano et al., 2026). What is clearer is the product problem: the optimization target was not aligned with the broader decision context the system shaped. The issue lies in the proxy choice, not only in its downstream effects.</p>

<p>The INFANT trial makes a different but related point through controlled evidence. Across more than 46,000 women in 24 maternity units, the decision-support system identified more abnormal cardiotocograph patterns than the control group, yet the trial found no significant difference in poor neonatal outcomes (INFANT Collaborative Group, 2017). This does not show that a differently designed product would necessarily have improved outcomes, but it does show that accurate signal detection did not translate into better clinical decisions. Identifying an abnormality and deciding when and how to intervene are different problems. The product was designed around the first and left the second largely to the clinical workflow.</p>
<br />

---

### Decision context determines acceptable performance
<p>Product performance is not just a property of the model. It is a property of the model inside a particular decision environment, including the task, the stakes, the user, the fallback path, and the degree of ambiguity in the setting (Afroogh et al., 2024). In high-stakes settings, especially where model output informs a more complex downstream action, “best model” is often the wrong standard. A model that performs well in isolation may still increase cognitive burden, obscure accountability, or produce outputs that users cannot translate into action. Good AI product design starts by defining success in the real decision context, not only in the metric that is easiest to optimize.</p>
<br />

---

### Stakeholders need different things
<p>AI systems are not evaluated through a single lens. Product teams may focus on efficiency, engagement, or scale. Users care whether the system helps them do their work. Affected parties may care about fairness, recourse, or downstream harm. In high-stakes settings, these are not interchangeable concerns (Vo et al., 2023; Afroogh et al., 2024). When a product is designed around one stakeholder’s task while leaving others structurally unaddressed, it builds in a failure mode that may not appear in benchmarks or early adoption but emerges later in use.</p>

<p>Facebook was designed around one stakeholder’s in-session experience. Researchers, regulators, and the public evaluated the same system in terms of information quality, exposure diversity, and broader social effects. The INFANT system centered the clinician reading the monitor, but the intervention decision also involved midwives, obstetricians, and institutional protocols the product did not integrate. In both cases, the product optimized for one stakeholder’s task while leaving the wider decision environment underdesigned (INFANT Collaborative Group, 2017; Vo et al., 2023).</p>
<br />

---

### Uncertainty should shape the product, not just the model
<p>Uncertainty is not a side detail. In many AI products it determines whether an output should be used at all. Interpretability and uncertainty-awareness help users rely on a system more appropriately, which makes uncertainty a product-design issue rather than a purely technical one (Tomsett et al., 2020).</p>

<p>The INFANT system flagged abnormalities but offered limited support for ambiguous alerts or cases where clinical context changed the meaning of the signal. Clinicians still had to determine urgency, intervention type, and timing. Surfacing uncertainty without helping users act on it does not resolve the product problem. The aim is to make uncertainty usable within the decision workflow the product enters.</p>
<br />

---

### What this changes for AI product development
<p>Both cases point to the same conclusion: product development cannot stop at model capability. The Facebook case shows what happens when the optimization target is misaligned with the decision context from the start. The INFANT case shows what happens when model capability is not matched by support for the decision that follows. In both, the gap is not simply in the model. It is in the decision environment the product creates or enters.</p>

<p>For AI teams, these cases suggest four practical priorities:</p>
<ul>
  <li><b>Define the decision before defining the metric:</b> identify the real decision the product influences, not only the task the model performs.</li>
  <li><b>Map the full decision workflow:</b> establish what user action follows the output, who else is involved, and what the product does or does not support at each step.</li>
  <li><b>Design for stakeholders outside the optimized metric:</b> identify who is affected by the product’s outputs but not represented in its design process.</li>
  <li><b>Make uncertainty usable at the point of decision:</b> define acceptable error in the real workflow and design uncertainty communication around that threshold.</li>
</ul>

<p>These are not secondary product questions. In high-stakes decision contexts, they determine whether an AI system supports better decisions in practice or mainly performs well in evaluation (Afroogh et al., 2024; Vo et al., 2023).</p>

---

### References
<div class="references">
  <p>Afroogh, S., Akbari, A., Malone, E., Kargar, M., & Alambeigi, H. (2024). Trust in AI: Progress, challenges, and future directions. Humanities and Social Sciences Communications, 11, 1568. https://doi.org/10.1057/s41599-024-04044-8</p>

  <p>Germano, F., Gómez, V., & Sobbrio, F. (2026). Ranking for engagement: How social media algorithms fuel misinformation and polarization. Journal of Public Economics, 255, 105589. https://doi.org/10.1016/j.jpubeco.2026.105589</p>

  <p>Guess, A. M., Malhotra, N., Pan, J., Barberá, P., Allcott, H., Brown, T., Crespo-Tenorio, A., Dimmery, D., Freelon, D., Gentzkow, M., González-Bailón, S., Kennedy, E., Kim, Y. M., Lazer, D., Moehler, D., Nyhan, B., Rivera, C. V., Settle, J., Thomas, D. R., … Tucker, J. A. (2023). How do social media feed algorithms affect attitudes and behavior in an election campaign? Science, 381(6658), eabp9364. https://doi.org/10.1126/science.abp9364</p>

  <p>INFANT Collaborative Group. (2017). Computerised interpretation of fetal heart rate during labour: A randomised controlled trial. The Lancet, 389(10080), 1719–1729. https://doi.org/10.1016/S0140-6736(17)30568-8</p>

  <p>Tomsett, R., Preece, A., Braines, D., Cerutti, F., Chakraborty, S., Srivastava, M., Pearson, G., & Kaplan, L. (2020). Rapid trust calibration through interpretable and uncertainty-aware AI. Patterns, 1(4), 100049. https://doi.org/10.1016/j.patter.2020.100049</p>

  <p>Vo, V., Chen, G., Aquino, Y. S. J., Carter, S. M., Do, Q. N., & Woode, M. E. (2023). Multi-stakeholder preferences for the use of artificial intelligence in healthcare: A systematic review and thematic analysis. *Social Science & Medicine, 338*, 116357. https://doi.org/10.1016/j.socscimed.2023.116357</p>
</div>