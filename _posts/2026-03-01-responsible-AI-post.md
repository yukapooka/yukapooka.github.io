---
layout: post
title: How People Actually Respond to AI - The Case for Calibrated Reliance
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

### Opening Tension
<p>Responsible AI is often framed as a problem inside the model: make it fairer, more transparent, more explainable, and better governed. But many important failures emerge later, in use — when people interpret outputs too confidently, dismiss them too quickly, or extend them beyond the conditions they were designed for (Dietvorst et al., 2015; Logg et al., 2019). Responsible AI is therefore not only a technical or policy problem. It is also a behavioral one.</p>

<p>Two examples make this easier to see. Tesla Autopilot shows how trust built under routine conditions can travel beyond the system’s actual limits. Diagnostic radiology AI shows that uncertainty communication, not just model accuracy, shapes whether reliance is appropriate.</p>
<br />

---

### The technical frame is incomplete
<p>Responsible AI discussions often center on fairness, transparency, explainability, and governance. Those are necessary, but they do not fully explain what happens once a system enters practice. What is often missing is the behavioral layer: how people interpret outputs, when they defer to them, when they override them, and when they treat the system as more general than it is. A model can perform well on paper and still produce poor outcomes if users misunderstand what it is for. Governance matters too, but a policy cannot guarantee good judgment in the moment. Real-world use is shaped by framing, habits, incentives, and context.</p>
<br />

---

### People do not respond to AI in one stable way
<p>The evidence does not support a simple story of people either trusting or distrusting AI. People may reject algorithmic advice after seeing it make a mistake, yet in other settings prefer algorithmic judgment over human judgment (Dietvorst et al., 2015; Logg et al., 2019). The more useful question is not whether users trust AI, but whether their reliance is calibrated to the task.</p>

<p>Tesla Autopilot illustrates one direction of miscalibration: overtrust, where confidence in the system exceeds what it warrants and monitoring falls away (Nordhoff et al., 2023). Interview findings suggest that users often shift into more passive, passenger-like roles when Autopilot performs reliably, taking on secondary tasks and treating the system as more capable than it is. Nordhoff and colleagues also note that the name “Autopilot” itself can raise expectations of autonomy beyond what the system actually provides. This is what makes the case useful: the problem is not only behavioral. It also sits in the product framing.</p>

<p>Miscalibration cuts both ways. Overreliance can lead users to miss warning signs or fail to notice when a system is out of scope. Underreliance can lead them to ignore useful advice or fail to benefit from a system that outperforms unaided judgment. The goal is not more trust. It is calibrated reliance: enough confidence to use the system well, and enough skepticism to question it when context requires it (Logg et al., 2019).</p>
<br />

---

### Uncertainty changes the problem
<p>When AI outputs are probabilistic or context-sensitive, users still have to decide how much weight to give them. In these settings, uncertainty communication is not a cosmetic feature; it helps shape whether reliance is appropriate (Tomsett et al., 2020).</p>

<p>Diagnostic radiology AI makes this visible in a different way. Experimental work in mammography shows that radiologists can exhibit automation bias when AI suggestions are wrong. Both inexperienced and highly experienced radiologists were significantly more likely to assign incorrect BI-RADS categories when an AI system provided incorrect labels (Dratsch et al., 2023). When outputs are presented as if they are definitive and uncertainty is not visible, users are more likely to follow plausible but incorrect advice. Trust calibration research suggests that making confidence information and system limitations more explicit can support more selective reliance (Tomsett et al., 2020). Taken together, the evidence points in the same direction: interfaces that communicate uncertainty more clearly are more likely to support calibrated use.</p>

<p>This shifts the design problem. AI outputs often require interpretation, not just execution. In high-stakes settings, the practical question is not whether a prediction is elegant, but whether it should be acted on. That depends not only on model quality, but on how the output is framed and understood.</p>

<br />

---

### The same pattern appears wherever stakes are high and decisions are consequential
<p>Healthcare is useful here because the stakes are high, uncertainty is common, and decisions are rarely made from model outputs alone. Reviews of AI implementation show that trust depends not only on technical performance but also on workflow fit, training, and accountability structures (Steerling et al., 2023; Vo et al., 2023).</p>

<p>The radiology example makes the behavioral layer concrete. A system can be accurate on average and still contribute to poor decisions if the interface does not communicate its limits or make uncertainty and failure modes visible (Dratsch et al., 2023). Conversely, an imperfect system can still be used well if its strengths and limitations are clear and users know when to rely on it and when not to (Tomsett et al., 2020).</p>

<p>This pattern is not unique to healthcare, though it should not be generalized too broadly. The radiology findings come from a specialized professional setting with trained users, formal accountability, and structured feedback. Similar dynamics are likely in other high-stakes expert settings, such as legal review, financial analysis, and infrastructure monitoring. Whether the same mechanisms apply in lower-stakes consumer settings is a separate question. Healthcare does not establish a universal claim, but it shows the pattern clearly in one important class of decisions.</p>
<br />

---

### What This Changes for Responsible AI
<p>The Tesla and radiology cases point in the same direction, though through different mechanisms. In Tesla’s case, the problem was not fully correctable through model improvement alone; it also depended on how the product communicated its operating limits. In radiology, the way uncertainty is expressed at the point of decision affects how outputs are used, independently of model accuracy. In both cases, behavioral response is part of system performance, not external to it.</p>

<p>For AI teams, these cases suggest four practical areas of focus:</p>
<ul>
  <li><b>Scope communication as a design requirement:</b> define where the system is reliable and where it is not, and make those boundaries visible in the product experience.</li>
  <li><b>Uncertainty display at the point of decision:</b> present confidence information in a form that supports selective reliance rather than uniform deference.</li>
  <li><b>Failure-inclusive onboarding:</b> expose users to cases where the system is wrong, not only where it performs well.</li>
  <li><b>Post-deployment behavioral monitoring:</b> track how users respond to the system after launch, not only how the model performs on benchmarks.</li>
</ul>

<p>These recommendations treat human response as part of the system, which is where it belongs. Responsible AI is not only about building systems that are technically sound. It is also about understanding the behavioral, organizational, and design conditions under which people use them well, badly, or somewhere in between (Dietvorst et al., 2015; Tomsett et al., 2020).</p>
<br />

---

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
