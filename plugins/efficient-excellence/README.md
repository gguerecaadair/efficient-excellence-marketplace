# Efficient Excellence — model routing

Opus triages every request and hands each sub-task to the model best suited to it: the heavy thinking goes to the strongest models at full reasoning depth; the routine parts go to fast, economical ones.

| Sub-task | Model | Agent |
|---|---|---|
| Triage, synthesis, hard/correctness-sensitive code | Opus 4.8 (xhigh) | hub · heavy-worker |
| Plans, architecture, adversarial & methodology reviews, complex synthesis | Fable (xhigh) | planner |
| Verification of important work | Opus / Fable (xhigh) | reviewer |
| Tables, formatting, simple Q&A, routine edits, tests | Sonnet 5 (medium) | worker |
| Bulk reading, searching, tracing across files | Haiku (low) | scout |

Bundled: the five agents above and a `routing` skill carrying the triage policy. Set once per person after install: default `model: opus` + `effortLevel: xhigh` (and, optionally, the cost meter). See the marketplace README for install and setup.
