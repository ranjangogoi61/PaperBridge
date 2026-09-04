PaperBridge
Turn confusing forms into conversations.
Problem
Government and financial forms — PAN, Aadhaar, Voter ID, Passport, Ration Card, Ayushman Card, Driving Licence, bank accounts, LIC policies, visas — are dense, jargon-heavy, and intimidating, especially for first-time applicants unfamiliar with formal English or bureaucratic language. I've filled out this exact kind of form for my own PAN card update, and for my brother's, from a remote village in Assam where digital form-filling isn't second nature. The usual process means manually decoding unfamiliar fields alone, often making errors — and for someone running a shared community device (like a cyber café), doing this for dozens of different people and document types every day.
Why WebMCP fits
Filling any of these forms is a multi-step action — name, father's name, date of birth, address, plus document-specific fields — that normally forces a person into many manual, confusing inputs. WebMCP lets an agent call the site's own registered tools directly, completing the entire flow from one natural-language request instead of decoding form after form of jargon.
How it creates a better experience
The person states their details once, in plain language. The agent handles the structured form-filling entirely through the site's own tools — no guessing which box means what, no decoding jargon. The human's only required action is a single Yes/No approval before anything is "submitted."
What's now possible that wasn't before
Previously, completing an unfamiliar form meant a person had to understand every field's terminology themselves, for every different document type. With PaperBridge:
They describe what they need in their own words, and the agent — using the website's own exposed capabilities, not by guessing at UI — fills the form and asks for one clear confirmation.
One unified interface covers 21 different document types — PAN (new/correction), Aadhaar (new/correction), Voter ID (new/correction), Passport (new/correction), Ration Card (new/correction), Ayushman Card (new/correction), Driving Licence (apply/renewal/address change), Income Certificate, Birth Certificate, Death Certificate, Bank Account Opening (across 10 major Indian banks with real account types), LIC Policy Application (across 8 real, currently-offered LIC plans), and Visa Applications (50+ countries, 5 visa types) — instead of needing a separate tool or process per document.
A searchable history lets one device serve many people over time (e.g. a shared community device or service centre) without losing track of who's application is at what stage.
A live document scanner (camera-based OCR) can auto-fill fields directly from an existing ID photo — the agent reads the document and fills matching fields, with the photo itself never stored anywhere, only the extracted text is used momentarily.
How WebMCP was implemented
Three core tools registered via document.modelContext.registerTool(), plus a fourth for scan-assisted filling:
Tool
Purpose
start_form(application_type)
Initializes a form session for any of the 21 supported document types, returns form_id
fill_field(form_id, field_name, value)
Fills one field; chains via form_id from start_form
validate_form(form_id)
Checks completeness (requirements vary per document type), gates the human-approval step
scan_document(form_id, extracted_text)
Extracts identity fields (name, DOB, PAN, Aadhaar number) from OCR text read off a photographed document, and fills matching fields — the photo itself is never passed or stored, only text
The agent performs all reasoning (deciding field values from natural language, or from document OCR); the website only exposes structured capabilities, validates, and renders — it never calls an LLM itself. A live Agent Activity Log records every tool call in order, and a Yes/No approval step (human-only, not agent-callable) gates final submission.
Architecture note: the application-type system is config-driven (a single APPLICATION_TYPES object) — every document type's required fields, correction sub-types, and UI labels are derived from one central config, rather than hardcoded per type. This made it possible to responsibly extend the project from 3 tools/1 document type to 21 document types without duplicating logic or introducing inconsistency.
Verification note: All tool logic — registration, chaining via form_id, field updates, validation rules per document type, and the OCR extraction logic — was independently verified via an automated Node.js/jsdom test harness covering every application type and edge case (empty fields, wrong document type, multi-session history). Live execution inside a WebMCP-enabled agent browser could not be fully verified from available testing devices at every stage — this project was built entirely on Android with no desktop/laptop access, and WebMCP's live agent support in ChatGPT is currently limited to the desktop app.
A note on the demo video and submission timeline
We were not aware the submission deadline had been extended until after our demo video was already recorded. Because of this, the demo video only shows the original PAN Application flow — it does not reflect the full scope of the project. Everything described above (Aadhaar, Voter ID, Passport, Ration Card, Ayushman Card, Driving Licence, Income/Birth/Death Certificates, Bank Account Opening across 10 banks, LIC policies, Visa applications across 50+ countries, the searchable history, the desktop-responsive layout, and the camera-based document scanner) was completed and added to the live project and repository on the day of the extended deadline, after the video was already recorded. The live URL and GitHub repository reflect the complete, current state of the project.
Architecture
Vanilla HTML/CSS/JavaScript — no framework, no backend
State: in-memory + localStorage (per-device, multi-session history)
OCR: Tesseract.js (client-side, no server, no image ever leaves the device or gets stored)
Deployed on Vercel
Responsive layout for both mobile and desktop use
Setup
Open index.html — no build step, no dependencies beyond the Tesseract.js CDN script (loaded automatically). Deployed live at: [live URL here]
Demo
[video link here — note: video shows only the original PAN Application flow; see note above]
License
MIT — see LICENSE.
