---
layout: post
title: How People Actually Respond to AI: The Case for Calibrated Reliance
date: 2026-03-01
#tags: responsible_ai
categories: responsible_ai behavioral_science ai_trust human_judgement
giscus_comments: false
related_posts: false
#toc:
#  beginning: true
---

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/thinking-man-article1.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Many Responsible AI discussions focus on fairness, transparency, or governance. But some of the most important failures emerge in how people interpret, react to, and act around AI systems in practice.
</div>
<br />

---
<br />

### Opening Tension
<p>Responsible AI is often discussed as if the main challenge lies inside the model: make it fairer, more transparent, more explainable, and better governed. But some of the most consequential failures — and the hardest to detect — happen later, when people interpret AI outputs, trust them too much, dismiss them too quickly, or use them outside the conditions they were designed for (Dietvorst et al., 2015; Logg et al., 2019). Responsible AI is therefore not only a technical or policy problem. It is also a human behavior problem.</p>

<p>Two examples help clarify this. Tesla Autopilot shows how trust built in routine conditions can be extended too far. Diagnostic radiology AI shows that uncertainty communication, not just model accuracy, shapes whether people rely on a system appropriately.</p>
<br />


### The technical frame is incomplete
<p>Responsible AI discussions often center on fairness, transparency, explainability, and governance. These are necessary, but they do not fully explain what happens once a system enters practice. What is often missing is the behavioral layer - how people interpret outputs, when they defer to them, when they override them, and when they assume the system is more general than it is. A model can perform well on paper and still produce poor outcomes if users misunderstand what it is for. Governance matters too, but a policy cannot guarantee good judgment in the moment. Real-world use is shaped by framing, habits, incentives, and context — none of which a policy document controls.</p>
<br />


### People do not respond to AI in one stable way
<p>The evidence does not support a simple story of people either trusting or distrusting AI. People may reject algorithmic advice after seeing it make a mistake, yet in other settings prefer algorithmic judgment over human judgment (Dietvorst et al., 2015; Logg et al., 2019). The more useful question is not whether users trust AI, but whether their reliance is calibrated to the task.</p>

<p>Tesla Autopilot illustrates one direction of miscalibration: overtrust, where confidence in the system exceeds what it warrants, encouraging overreliance and reduced monitoring (Nordhoff et al., 2023). Interview findings suggest that users often slide into more passive, passenger-like roles when Autopilot performs reliably, taking on secondary tasks and treating the system as more capable than it is. The problem is that trust built under familiar conditions was carried over into situations where those conditions no longer held. It is worth noting that the Tesla case is not a pure behavioral story — the product name "Autopilot" has itself been shown to raise expectations of autonomy beyond what the system delivers, making this partly a product design and naming problem as well as a reliance problem (Nordhoff et al., 2023).</p>

<p>Miscalibration cuts both ways. Overreliance can lead users to miss warning signs or fail to notice when a system is out of scope. Underreliance can lead them to ignore useful advice or fail to benefit from a system that outperforms unaided judgment. The goal, then, is not more trust. It is calibrated reliance: enough confidence to use the system well, and enough skepticism to question it when context requires it (Logg et al., 2019).</p>
<br />


### Uncertainty changes the problem
<p>When AI outputs are probabilistic or context-sensitive, users still have to decide how much weight to give them. In these settings, uncertainty communication is not a cosmetic feature — it shapes whether reliance is appropriate (Tomsett et al., 2020).</p>

<p>Diagnostic radiology AI illustrates this clearly. Experimental work in mammography shows that radiologists can exhibit automation bias when AI suggestions are wrong. Both inexperienced and highly experienced radiologists were significantly more likely to assign incorrect BI-RADS categories when an AI system provided incorrect labels (Dratsch et al., 2023). When AI outputs are treated as definitive and uncertainty is not visible, users tend to follow plausible but incorrect advice. The design inference — that making confidence information and system limitations more explicit can help clinicians defer where the system is strong and apply independent judgment where it is not — draws on trust calibration research more broadly rather than from the radiology study alone (Tomsett et al., 2020). The two points together suggest a direction: surfaces that communicate uncertainty are likely to produce more selective reliance.</p>

<p>This shifts the design problem. AI outputs often require interpretation, not just execution. In high-stakes settings, the practical question is not whether a prediction is elegant, but whether it should be acted on — and that depends not only on model quality, but on how the output is framed and understood.</p>

<br />


### The same pattern appears wherever stakes are high and decisions are consequential
<p>Healthcare is useful here because the stakes are high, uncertainty is common, and decisions are rarely made from model outputs alone. Reviews of AI implementation show that trust depends not only on technical performance but also on workflow fit, training, and accountability structures (Steerling et al., 2023; Vo et al., 2023).</p>

<p>The radiology example makes the behavioral layer concrete. A system can be accurate on average and still contribute to poor decisions if the interface does not communicate the limits of that accuracy or make uncertainty and potential failure modes visible to the user (Dratsch et al., 2023). Conversely, an imperfect system can still be used well if its strengths and limitations are clearly communicated and users know when to rely on it and when not to (Tomsett et al., 2020).</p>

<p>This pattern is not unique to healthcare, but caution is warranted in how far it generalizes. The radiology findings come from a specialized professional context — trained clinicians, formal accountability, high decision stakes, and structured feedback loops. The behavioral dynamics are likely present in other high-stakes professional settings where expertise is required to interpret AI outputs: legal review, financial analysis, infrastructure monitoring. Whether the same mechanisms operate in lower-stakes, lower-expertise consumer contexts is a separate and open question. Healthcare does not prove a universal claim. It demonstrates the pattern clearly enough to take seriously in analogous settings.</p>
<br />


### What This Changes for Responsible AI
<p>The Tesla and radiology cases point in the same direction, though they arrive there differently. Tesla's miscalibration problem was not fully correctable by improving the model — it required changing how the product communicated its operating boundaries, which is a design and naming decision as much as a technical one. The radiology evidence suggests that how uncertainty is expressed at the point of decision shapes the quality of the decision made, independently of model accuracy. In both cases, the behavioral response is part of the system's performance, not external to it.</p>

<p>For AI teams, the Tesla and radiology cases suggest four specific areas of focus:</p>
<ul>
  <li><b>Scope communication as a design requirement, not a disclaimer:</b> Define explicitly where the system is reliable and where it is not, and make those boundaries visible in the product experience itself. If the product name or interface creates expectations that exceed what the system delivers, that is a design problem, not a user error.</li>
  <li><b>Uncertainty display at the point of decision:</b> Present confidence information where the decision is actually made. Present it in a form that supports selective reliance rather than uniform deference. Outputs presented as definitive predictions will be treated as such. The goal is not to overwhelm users with caveats but to make the system's limitations legible.</li>
  <li><b>Failure-inclusive onboarding:</b> Expose users to cases where the system is wrong, not only cases where it performs well. Reliance built on a selective picture of system capability is inherently miscalibrated. Seeing failure modes in controlled conditions produces more stable trust than discovering them in consequential ones.</li>
  <li><b>Post-deployment behavioral monitoring:</b> Track how users are actually responding to the system after launch — not just whether the model is performing on benchmarks. Patterns of overreliance and underreliance are observable, and when identified, they require a defined response -  interface adjustment, retraining, or workflow redesign. </li>
</ul>

<p>These recommendations treat human response as part of the system, which is where it belongs. Responsible AI is not only about building systems that are technically sound. It is also about understanding the conditions — behavioral, organizational, and design — under which people use them well, badly, or somewhere in between (Dietvorst et al., 2015; Tomsett et al., 2020).</p>
<br />


### References
<div class="references">
  <p>Dietvorst, B. J., Simmons, J. P., & Massey, C. (2015). Algorithm aversion: People erroneously avoid algorithms after seeing them err. Journal of Experimental Psychology: General, 144(1), 114–126. https://doi.org/10.1037/xge0000033</p>

  <p>Dratsch, T., Chen, X., Rezazade Mehrizi, M., Lüdemann, L., Santo, G., Metz, K. A., Körner, M., Persigehl, T., Maintz, D., & Pinto dos Santos, D. (2023). Automation bias in mammography: The impact of artificial intelligence BI-RADS suggestions on reader performance. Radiology, 307(4), e222176. https://doi.org/10.1148/radiol.222176</p>

  <p>Logg, J. M., Minson, J. A., & Moore, D. A. (2019). Algorithm appreciation: People prefer algorithmic to human judgment. Organizational Behavior and Human Decision Processes, 151, 90–103. https://doi.org/10.1016/j.obhdp.2018.12.005</p>

  <p>Nordhoff, S., Lee, J. D., Calvert, S. C., Berge, S., Hagenzieker, M., & Happee, R. (2023). (Mis-)use of standard Autopilot and Full Self-Driving (FSD) Beta: Results from interviews with users of Tesla's FSD Beta. Frontiers in Psychology, 14, 1101520. https://doi.org/10.3389/fpsyg.2023.1101520</p>

  <p>Steerling, E., Siira, E., Nilsen, P., Svedberg, P., & Nygren, J. (2023). Implementing AI in healthcare — the relevance of trust: A scoping review. Frontiers in Health Services, 3, 1211150. https://doi.org/10.3389/frhs.2023.1211150</p>

  <p>Tomsett, R., Preece, A., Braines, D., Cerutti, F., Chakraborty, S., Srivastava, M., Pearson, G., & Kaplan, L. (2020). Rapid trust calibration through interpretable and uncertainty-aware AI. Patterns, 1(4), 100049. https://doi.org/10.1016/j.patter.2020.100049</p>

  <p>Vo, V., Chen, G., Aquino, Y. S. J., Carter, S. M., Do, Q. N., & Woode, M. E. (2023). Multi-stakeholder preferences for the use of artificial intelligence in healthcare: A systematic review and thematic analysis. Social Science & Medicine, 338, 116357. https://doi.org/10.1016/j.socscimed.2023.116357</p>
</div>
