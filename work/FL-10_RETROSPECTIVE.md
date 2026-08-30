# Final Retrospective — From Week 1 to the Finished Build

When I started this track, my goal was straightforward: learn enough about AI and machine learning to build something real that I could explain to another person. I was much more focused on getting an artifact working than I was on the discipline behind it. Over the track, that changed. I learned that a useful AI/ML project is not just a model or a polished interface; it is a chain of decisions that another person can inspect.

My main project became a CTR / Engagement Opportunity Scoring system for search content. The practical problem was prioritization: an SEO or content reviewer cannot investigate every page with equal depth. I wanted to use search visibility and engagement signals to create a ranked list of pages that deserved attention first. That gave the project a concrete user and a concrete decision instead of turning it into a generic “predict SEO performance” exercise.

The biggest change in how I work was learning to treat data definitions as part of the model. I had to decide what one row represented, which signals were available at decision time, what the target meant, and what information had to be excluded. The most important example was the exploratory model result that looked extremely good. The model achieved an MAE of 0.000016 compared with a baseline MAE of 0.012917. At first glance, that looked like a huge success. Looking more carefully, I realized that the model had access to clicks and impressions while predicting CTR. Since CTR is calculated directly from those values, the model was effectively being given the answer. That result was leakage, not a breakthrough. Keeping that failure visible was more valuable than hiding it.

The second major change was learning to turn technical output into a decision. A score by itself is not very useful to a content reviewer. The useful artifact is a ranked queue with an action and a reason code, followed by human review. That framing changed the project from “I trained a model” to “I built a repeatable prioritization workflow.”

The third change was learning to ship and communicate. I built a public portfolio, deployed it on Netlify, created a research-paper presentation for the capstone, and documented the work in the repository. I also learned that deployment and presentation are part of the engineering work: a project that nobody can open, understand, or reproduce is much less useful than one that can be inspected.

If I continued the project, the next thing I would build is a genuinely leakage-safe future-window evaluation. I would separate decision-time features from the next-period outcome, make the validation split explicitly time-aware, and compare the resulting model with the transparent baseline on the same held-out period. I would also improve the recommendation layer so that the reason codes explain not just that a page is ranked highly, but which observable evidence caused the ranking.

The three most transferable things I learned are:

1. **Define the problem before choosing the model.** A clear decision and unit of analysis prevent a lot of unnecessary complexity.
2. **Treat leakage checks as a first-class part of ML.** A great metric is meaningless if the answer has leaked into the inputs.
3. **Make outputs usable by a human.** A model becomes useful when its output is understandable, reviewable, and connected to a real decision.

The biggest lesson I would give my Week-1 self is: do not confuse something that runs with something that is trustworthy. Running code is the beginning. Checking assumptions, testing failure modes, explaining the result, and being honest about what the evidence does not prove are what make the work credible.
