# PaperBridge

**Turn confusing forms into conversations.**

## Problem

Government-style forms (like a PAN application) are dense, jargon-heavy, and intimidating — especially for first-time applicants unfamiliar with formal English or bureaucratic language. I've filled out this exact kind of form for my own PAN card update, and for my brother's, from a remote village in Assam where digital form-filling isn't second nature. The usual process means manually decoding unfamiliar fields alone, often making errors.

## Why WebMCP fits

Filling a form is a multi-step action — name, father's name, date of birth, address — that normally forces a person into six separate manual inputs. WebMCP lets an agent call the site's own registered tools (`start_form`, `fill_field`, `validate_form`) directly, completing the entire flow from one natural-language request instead of six manual fields.

## How it creates a better experience

The person states their details once, in plain language. The agent handles the structured form-filling entirely through the site's own tools — no guessing which box means what, no decoding form jargon. The human's only required action is a single Yes/No approval before anything is "submitted."

## What's now possible that wasn't before

Previously, completing an unfamiliar form meant a person had to understand every field's terminology themselves. With PaperBridge, they describe what they need in their own words, and the agent — using the website's own exposed capabilities, not by guessing at UI — fills the form correctly and asks for one clear confirmation.

## How WebMCP was implemented

Three tools registered via `document.modelContext.registerTool()`:

| Tool | Purpose |
|---|---|
| `start_form(application_type)` | Initializes a form session, returns `form_id` |
| `fill_field(form_id, field_name, value)` | Fills one field; chains via `form_id` from `start_form` |
| `validate_form(form_id)` | Checks completeness, gates the human-approval step |

The agent performs all reasoning (deciding field values from natural language); the website only exposes structured capabilities, validates, and renders — it never calls an LLM itself. A live Agent Activity Log records every tool call in order, and a Yes/No approval step (human-only, not agent-callable) gates final submission.

**Verification note:** All three tools were independently verified via automated DOM simulation — registration, sequential execution, `form_id` chaining, and live UI updates all confirmed working correctly. Live execution inside a WebMCP-enabled agent browser could not be independently verified from available testing devices at submission time — WebMCP remains an early-preview browser feature with limited current device/app support.

## Architecture
## Operator History (for shared-device use, e.g. a service center)

Since one device may be used by an operator to help multiple people (e.g. a cyber café or common service center filling PAN forms for different customers), PaperBridge keeps a searchable local history of past applications:

- Every application is automatically saved to `localStorage` as it progresses
- A history drawer (☰ icon, top-right) lists all past applications with name, status, and timestamp
- Search filters by applicant name
- Tapping a past entry reloads it — fields, activity log, and approval status all restore exactly as they were

This is a human-facing UI feature only — it is not a WebMCP tool and is never called by the agent. It exists so an operator can pick up where a previous customer's session left off, without losing prior work.
- Vanilla HTML/CSS/JavaScript — no framework, no backend
- State: in-memory + `localStorage` (single-session demo by design)
- Deployed on Vercel

## Setup

## Setup

Open `index.html` — no build step, no dependencies. Deployed live at: **https://paper-bridge-oo49.vercel.app**
## Demo

[video link here]

## License

MIT — see `LICENSE`.
