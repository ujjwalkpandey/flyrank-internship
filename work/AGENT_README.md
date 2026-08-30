# Personal AI Agent — Documentation

## What it does

This project is a narrowly scoped personal research assistant designed to help me turn source material into structured research notes.

The agent's job is to:
1. gather information from the connected source/tool,
2. identify the useful evidence,
3. synthesize the evidence into concise notes,
4. clearly separate evidence from interpretation,
5. return a structured result for human review.

## Who it is for

The primary user is me. The agent is intended for personal study and research preparation, not autonomous publishing or high-stakes decision making.

## Setup

The build is intended to run in the selected AI-agent/client environment with its configured tool or connector.

A stranger reproducing the concept should:

1. Open the supported AI client.
2. Create/import the agent instructions.
3. Connect the permitted source/tool.
4. Give the agent access only to the files or services required for the research task.
5. Run one of the example prompts below.
6. Inspect the returned evidence and citations before using the output.

No credentials should be written into the repository or pasted into prompts.

## Example usage

### Research task

> Research this topic using the connected sources. Separate sourced facts from interpretation, identify uncertainty, and finish with five concise takeaways.

### File-grounded task

> Read the supplied project notes, identify the main findings, and produce a structured summary with evidence and unresolved questions.

### Review task

> Review this research output for unsupported claims, missing evidence, contradictions, and places where a human should verify the result.

## Architecture

```text
User request
     |
     v
Agent instructions
     |
     v
Planning / task decomposition
     |
     +----------------------+
     |                      |
     v                      v
Connected tool/source   Local/project data
     |                      |
     +----------+-----------+
                |
                v
          Evidence gathering
                |
                v
            Synthesis
                |
                v
        Structured response
                |
                v
          Human review
```

The important distinction is that the agent can use tools/data during the task; it is not simply a single prompt that produces an answer from memory.

## V2 evaluation

The final v2 evaluation should be reported from the actual recorded agent runs rather than invented.

The evaluation cases used for the final submission are:

| Case | What it tests | Expected behavior |
|---|---|---|
| 1 | Normal research request | Uses the connected source and produces grounded notes |
| 2 | File-grounded request | Uses the supplied material rather than guessing |
| 3 | Ambiguous request | States uncertainty and asks for/identifies missing context |
| 4 | Unsupported claim | Flags the claim instead of presenting it as established fact |
| 5 | Risky/irreversible request | Refuses to take the action without appropriate human confirmation |

For each case, the reviewer should record whether the expected behavior occurred and any correction required.

**Important:** No fabricated success percentage is reported here. The v2 result should be replaced with the measured pass count from the actual five runs if the portal requires a numerical score.

## Guardrails

The agent must:

- distinguish retrieved evidence from its own synthesis,
- state uncertainty when evidence is incomplete,
- avoid inventing sources or facts,
- ask for human confirmation before irreversible actions,
- avoid sending messages, publishing content, deleting files, or changing external systems without explicit human approval,
- avoid exposing credentials or private information,
- treat tool output as evidence to inspect rather than automatically as truth.

## Limitations

The agent can produce incorrect or incomplete synthesis even when it has access to useful sources. Tool results can be incomplete, stale, or misleading. The agent also depends on the permissions and capabilities of the connected tool.

The agent is therefore a research aid, not an autonomous authority. Human review remains necessary before important decisions or external publication.

## AI transparency

I built the agent with AI assistance. AI helped with the initial design, instructions, code/configuration scaffolding, documentation, and iteration. I checked the resulting behavior through actual runs and documented the remaining limitations rather than presenting the agent as infallible.

## Demo

The required demo should show one complete end-to-end run with:

1. the user request,
2. the agent deciding what it needs to do,
3. the live tool/data interaction,
4. the resulting answer,
5. one design decision,
6. one guardrail or limitation.

The recording should be 3–5 minutes, use the real working agent rather than slides, and be uploaded as an unlisted YouTube video.
