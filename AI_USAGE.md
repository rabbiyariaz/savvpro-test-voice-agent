# AI Usage

## 1. Tools used

- **GitHub Copilot:** Code generation for NLU regex, the finite-state machine, FastAPI wrapper, React frontend, and pytest suite.
- **Claude:** Planning, use-case selection, edge-case design, prompt drafting, and debugging guidance.

## 2. How they helped

- Scaffolded the brain modules and their initial interfaces.
- Generated the test suite and scenario coverage.
- Wrote the FastAPI endpoints and React page.
- Suggested fixes during debugging.

## 3. Where they got things wrong

| Issue | What the AI did | Fix |
|---|---|---|
| Phone number parsed as a date | `dateparser` misread a phone number as a date. | Added digit-length guards and slot-directed phone parsing. |
| Filler stored as `patient_name` | Stored “whatever works” as the patient name. | Added slot-directed parsing: accept a bare name only when `patient_name` is the pending slot. |
| Change phrase stored as a name | Stored “actually make it Friday” as a patient name. | Added change detection before name capture. |
| Strict time parsing | Failed on “p.m”, “3.30”, and “around 2 ish”. | Loosened parsing, stripped dots and filler, and accepted a dot as a minute separator. |
| Confirmation regression | Broadening confirmation words caused a mid-call change to be caught as `confirm_no`. | Fixed ordering so slot changes take precedence over `confirm_no`. |
| Availability message conflation | Treated outside-working-hours requests as if the slot were taken. | Separated the two cases into distinct messages. |

## 4. Key takeaway

AI accelerated scaffolding and test generation, but every bug above was found through my own adversarial manual testing, not by the AI.
I directed the decision logic and edge-case design; the AI implemented to that specification.

## 5. Token usage

GitHub Copilot is subscription-based and does not expose per-request token counts, so exact Copilot token usage is unavailable. A usage screenshot is attached below.

**Copilot usage**

Claude usage is reported separately if per-request usage data is available.
