# Final Agent Demo — 3–5 Minute Recording Script

## 0:00–0:30 — What this is

“I'm showing my personal AI research agent. Its job is to help me gather and synthesize information using a connected source or tool. I designed it as a narrow research assistant rather than a general autonomous agent.”

## 0:30–1:15 — The request

Show the real agent.

Say:

“I'll give it a research task. The important part is that it has access to a tool/source, so it can do something that ordinary chat without that connection could not do.”

Enter a real research request.

## 1:15–2:15 — Live tool use

Show the tool call / connected source being used.

Say:

“Here the agent is gathering evidence through its connected tool. I want the evidence separated from interpretation because a fluent answer is not automatically a trustworthy answer.”

Let the run complete.

## 2:15–3:00 — Result

Read the important part of the output.

Say:

“The output is structured into evidence, synthesis, and uncertainty. This is deliberate: the user should be able to inspect what came from the source rather than treating every sentence as equally certain.”

## 3:00–3:40 — Design decision

Say:

“One design decision I made was to keep the agent narrow. Instead of trying to make it an all-purpose autonomous assistant, I gave it one job: source-grounded research and synthesis. That makes it easier to evaluate and easier to understand when it fails.”

## 3:40–4:30 — Guardrail / limitation

Say:

“One limitation is that the agent can still misunderstand or incompletely synthesize its sources. It therefore does not get permission to publish, delete, send, or make irreversible changes automatically. Human review stays in the loop.”

## 4:30–5:00 — Close

Say:

“The main lesson from building this was that an agent is not just a chatbot with a fancy prompt. The useful difference is the ability to work through tools and data as part of a defined task, with evaluation and guardrails around that behavior.”
