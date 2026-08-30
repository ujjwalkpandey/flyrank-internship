# Build-in-public post

I just finished a search-intelligence ML capstone built around a simple question:

**Which pages should an SEO/content reviewer investigate first for CTR and engagement opportunity?**

I used the FlyRank ML Internship search-performance warehouse to build a page-level prioritization workflow, compare a transparent baseline with a modeling approach, and turn the output into a ranked human-review queue.

The most important part of the project was actually a failure.

My first model run looked fantastic: baseline MAE was 0.012917 and model MAE was 0.000016. Then I checked the features. The model was using clicks and impressions to predict CTR, even though CTR is directly calculated from those values.

So I rejected the result.

That changed the project from “look at my amazing metric” to a much more useful lesson: **ML quality depends on whether the experiment is honest, not just whether the score is good.**

The final framing is decision support, not automatic SEO action. A high-ranked page is a candidate for human investigation, not proof that its title, metadata, or content needs to change.

I also shipped the work as a public research artifact and portfolio case study.

Repository:
https://github.com/ujjwalkpandey/flyrank-internship

Portfolio:
https://dynamic-chaja-8332db.netlify.app/

Research paper:
https://ujjwalkpandey.github.io/flyrank-internship/
