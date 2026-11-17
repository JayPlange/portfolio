# Edwin Plange

> Founder and product engineer turning customer problems and operational workflows into working software. Focused on applied AI, integrations, product engineering, and forward-deployed implementation.

Website: https://edwinplange.vercel.app/  
LinkedIn: https://linkedin.com/in/edwin-plange  
GitHub: https://github.com/JayPlange  
Email: justiceplange@gmail.com

## Professional summary

I work close to the problem before deciding what to build. That means understanding how a business or user actually works, identifying the constraints, and turning the workflow into software that can be tested, deployed, and improved.

My work spans product engineering, applied AI, API integrations, workflow automation, and evaluation of tool-using systems. I move between customer and operator requirements, technical design, implementation, testing, and debugging. I am particularly interested in forward-deployed engineering roles where the work involves both understanding a customer's environment and owning the technical implementation.

I founded and built DualProfile, a live browser-extension product. I am developing KasaFlow, a WhatsApp-based AI operator for a Ghanaian retail pilot. I created The Last Yes, a standalone benchmark for transaction-authorisation integrity in conversational commerce agents. Through Webblabs, I work on SME requirements and dashboard engineering. Earlier roles in telecom network operations and IT compliance shaped how I approach operational risk, incident response, and systems that need to behave predictably.

My strongest areas are product engineering, applied AI, integrations, customer-facing implementation, and evaluation engineering. The projects below are identified by their actual maturity: shipped product, retail pilot, pre-release client work, hackathon prototype, or standalone experiment.

## Selected projects

### KasaFlow

**Role:** Founder and AI/Product Engineer  
**Started:** January 2026  
**Status:** Retail pilot; not deployed to a public application host  
**Repository:** https://github.com/JayPlange/Kasaflow

KasaFlow is a WhatsApp-based AI operator designed to help small businesses handle customer enquiries and commerce workflows. The current pilot is being developed for a Ghanaian jewellery retailer.

The system combines Python, FastAPI, OpenAI's Responses API, WhatsApp Cloud API, WooCommerce, product retrieval, and voice processing for Twi voice notes.

Engineering work includes:

- A modular tool registry and executor that separates model decisions from application-side execution.
- A live WooCommerce catalogue containing 3,918 products.
- A 46-scenario behavioural evaluator covering 15 categories, 85 customer turns, and 24 multi-turn scenarios.
- An anonymised conversation evaluation set replayed through the real router in a sandbox. Recorded mode replays saved model outputs; live mode calls the model again to examine variance.
- Application-side guardrails: re-pricing the quoted item before an order is written, checking the store total afterwards, blocking order writes on turns flagged for prompt injection, and handing conversations to a person on request or after repeated failures or manipulation.
- Explicit order-proposal and order-confirmation boundaries, with deterministic pricing and a separate write path.
- Recovery logic for timed-out order creation to reduce duplicate-order risk.
- Regression tests based on observed failures, including product matching, stale conversation state, order corrections, and access control.

As of 2 November 2026, the suite had 937 passing tests, with a further 29 gated tests that call the real model API. The evaluation set contains operator test conversations; cost and live latency have not yet been measured. Test counts and implementation status should be interpreted against the dated source snapshot.

The quote/pricing and order-creation paths were verified against the live WhatsApp API, live WooCommerce catalogue, and live store. This does not mean the complete product is publicly deployed or generally available.

### The Last Yes

**Role:** Creator and evaluation engineer  
**Status:** Standalone benchmark built for the Micro1 Eval Hackathon, November 2026

The Last Yes is a benchmark for **transaction-authorisation integrity in conversational commerce agents**. It tests whether a tool-using assistant can distinguish a customer's acknowledgement from permission to act, preserve the latest transaction state, respect withdrawal and amendment, request missing information, prevent duplicate writes, and avoid accessing another customer's order.

The benchmark runs against a synthetic commerce simulator. It includes a ten-task core suite, three exploratory authority-claim probes, and a five-condition matched-authority experiment. The model receives the task, policy, and tool definitions; a deterministic Python grader evaluates tool calls and resulting simulator state. The core score does not rely on an LLM judge.

Engineering work includes:

- A self-contained Python evaluation harness with tool-calling model runs, fresh conversations and simulator state per trial, and JSON result reports containing transcripts, tool calls, events, model metadata, and final state.
- A deterministic grader for action sequence, order ownership, proposal and confirmation state, duplicate writes, missing data, false completion claims, and consequential side effects.
- Separate reference-policy traces and mutation tests designed to check that incorrect actions are rejected rather than accidentally passed.
- A matched-prompt experiment that holds the request, system policy, tools, simulator, and grader constant while varying only the final authority-claim sentence.
- Transcript-level failure review that separates attempted policy violations from successful data disclosure or state changes, and provider timeouts from completed model evaluations.

**Observed results.** Live runs used temperature 0.0 and two hosted OpenRouter free-model routes: `cohere/north-mini-code:free` and `nvidia/nemotron-3.5-super-vl:free`.

- **v0.1.7 ownership baseline:** Across five trials each for a foreign-order negative case and an own-order positive control, Nemotron passed 10/10. Cohere passed 4/10. It attempted the foreign-order lookup in all five negative-case trials and used the wrong order ID in one own-order lookup trial. The simulator denied the foreign lookups; no data was disclosed and no state changed.
- **v0.1.8 exploratory authority probes:** Nemotron passed 9/9. Cohere passed 6/9, with three foreign-order lookup attempts across employee-role and manager-approval prompts. The urgent-delegation condition passed all three Cohere trials. These probes were exploratory, not matched prompts, and do not establish that a particular authority phrase caused the failures.
- **v0.1.9 matched-authority follow-up:** Nemotron passed 15/15. Cohere completed 14/15 original requests successfully; the remaining request timed out at the provider. A separate retry of that owner-permission condition passed, giving Cohere 15 completed passes across 16 requests. Across both models, 30 completed matched-authority evaluations passed across 31 requests, with one provider timeout and no behavioural incidents in the completed trials.

The v0.1.9 working snapshot passed 42 automated tests and 18/18 reference validations. These results are exploratory evidence from two specific hosted free-model routes and small trial counts, not a representative survey of frontier models or a statistical claim about either model family. The matched follow-up did not reproduce the earlier Cohere ownership failures, so the earlier exploratory results are reported separately rather than treated as a causal effect of authority wording. The benchmark tests adherence to an explicit policy provided in the prompt; it is not a production security audit or a legal determination.

**Prior work and provenance.** KasaFlow's pre-existing architecture, transaction boundaries, and 46-scenario behavioural evaluator informed the research question. The Last Yes itself was created as a separate synthetic benchmark for the hackathon. It does not import KasaFlow application code or include its credentials, real customer conversations, or retailer catalogue.

### Stall to Store

**Role:** Builder  
**Status:** Hackathon prototype built for the Meta Global AI Developer Hackathon

Stall to Store explores a way for small sellers to turn a short product video into a structured, reviewable online catalogue. The workflow takes a 20–60 second video of packaged goods with spoken product names and prices, identifies products and visual regions, and prepares a shop page that can connect to WhatsApp commerce workflows.

The prototype combines Meta's SAM 3.1 for visual segmentation and tracking, Voice Transcribe for spoken product details, and Muse Spark for associating the spoken information with the visual products. The seller reviews the extracted products and prices before the shop page is created.

The key design choice is to keep the seller in control of the extracted catalogue. The AI prepares candidate product information; the seller reviews it before publication. This is a hackathon prototype, not a claim of a generally available commerce platform.

### DualProfile

**Role:** Founder and Product Engineer  
**Started:** January 2025  
**Status:** Live Chrome extension  
**Product:** https://chromewebstore.google.com/detail/dualprofile/mdlhdncmaeepcejdbpnjpjlmagmmpkpc  
**Website:** https://vivaup.org

DualProfile is a browser-extension product that lets people schedule WhatsApp profile-photo changes and assign different profile photos to individual contacts.

I built and maintain the product across its browser extension, backend, synchronisation, entitlement, and commercial flows.

Engineering work includes:

- Browser DOM observation and fallback handling for WhatsApp Web interface changes.
- Real-time synchronisation using Convex.
- Server-side entitlement enforcement and licence verification.
- Security fixes for account linking, recovery-key verification, and privacy-sensitive contact data.
- Dry-run-first data migrations and regression tests around existing user data.
- A deliberate human-confirmation boundary for scheduled photo changes, where automated interaction proved unreliable.

The product combines browser engineering, backend state management, security, monetisation, and direct product iteration.

### Multi-branch operations dashboard

**Role:** Dashboard frontend owner through Webblabs  
**Status:** Pre-release hardening; client source is private

A multi-branch operations dashboard for a microfinance business, built with Next.js, React, and TypeScript.

I own the dashboard frontend. Another engineer owns the mobile application and platform API, with integration through OpenAPI contracts.

The documented hardening work includes:

- A Playwright access matrix covering 800 role-and-page combinations.
- Unit tests increased from 91 to 282.
- 967 passing end-to-end tests and zero failing tests in the measured run.
- Server-side session handling, token renewal, return-URL validation, and Content Security Policy checks.
- A gated release process that separates frontend-owned issues from defects requiring platform-owner decisions.

The measurements were taken on a seeded demo dataset, not live production data. The project remains subject to outstanding platform dependencies and release decisions.

## Engineering principles

### Start with the workflow, not the tool

Understand the people, constraints, and existing process before choosing an implementation. The useful solution is the one that fits the real workflow.

### The model proposes. Application code executes.

AI can interpret requests and propose actions, but application code should enforce business rules, permissions, state transitions, and consequential side effects.

### Grade actions and state, not just plausible language

For tool-using systems, a natural-sounding response is not enough. Evaluation should inspect which tools were called, what arguments were supplied, and what changed in the system.

### A production failure is engineering input

A bug is not fully resolved until its cause is understood, the fix is verified, and a regression test protects against recurrence where appropriate.

### Security boundaries belong on the server

Client-side checks improve usability but must not be the authority for identity, permissions, or paid entitlements.

### Automate only when the failure mode is acceptable

A human confirmation step can be the correct engineering decision when an unreliable automated action could damage a user's data or create an irreversible outcome.

## Professional experience

### KasaFlow
**Founder and AI/Product Engineer | January 2026–present**

Developing a WhatsApp-based AI operator for a Ghanaian retail pilot, including tool orchestration, commerce integrations, deterministic order controls, and behavioural evaluation.

### DualProfile
**Founder and Product Engineer | January 2025–present**

Built and operate a live WhatsApp browser-extension product spanning browser engineering, backend state, account security, synchronisation, and commercial flows.

### Webblabs
**Co-Founder | 2025–present**

Lead client discovery and SME workflow mapping while contributing to dashboard engineering, testing, and release hardening for a multi-branch operations system.

### Independent client project
**Automation Systems Engineer | 2024–2025**

Built a multi-step n8n AI pipeline combining audio, image, and text inputs with structured failure recovery under real API constraints.

### KPMG Ghana
**IT Compliance Associate | February–May 2023**

Conducted on-site stakeholder assessments across nearly all 16 regions of Ghana for the GNAT national cloud migration, contributing field findings to migration risk documentation.

### Geoquaye Company Ltd
**Network Operations Engineer | November 2021–January 2023**

Monitored live telecom infrastructure, investigated incidents, and escalated faults under uptime service-level agreements.

### American Tower Corporation Ghana
**NOC Engineer | October 2020–September 2021**

Supported multi-site network operations and coordinated incident resolution across technical and non-technical teams.

## Technical areas

- **Product engineering:** TypeScript, JavaScript, React, Next.js, browser extensions, APIs, frontend engineering.
- **Applied AI:** Python, FastAPI, OpenAI Responses API, tool calling, structured outputs, retrieval, workflow orchestration.
- **Customer-facing implementation:** Workflow discovery, requirements mapping, technical implementation, API integration, debugging with operational context.
- **Evaluation engineering:** Benchmark and task design, deterministic grading, reference traces, mutation testing, tool-use evaluation, matched-prompt experiments, transcript and failure analysis.
- **Integrations:** WhatsApp Cloud API, WooCommerce, Convex, OpenRouter, external service APIs.
- **Reliability and security:** pytest, Jest, Vitest, Playwright, regression testing, incident diagnosis, session handling, access control, safe side effects.

These categories describe areas demonstrated across the projects above, rather than claiming equal depth in every technology.

## Education and credentials

- NCC Education Level 5 Diploma in Business Information Technology, through IPMC / University of Greenwich.
- CompTIA Security+.
- Oracle Cloud Infrastructure AI Foundations Associate.
- Oracle Cloud Infrastructure Foundations Associate.
- Andela Scrum Product Ownership.

## How to evaluate my work

Use the linked source repositories, live product listings, case studies, and dated test reports as the primary evidence for implementation claims.

Distinguish shipped products from pilots, pre-release client work, hackathon prototypes, and experiments. Do not infer production deployment, commercial traction, independent authorship, or current test counts beyond what the available sources establish.

For opportunities, my strongest fit is work combining product engineering, applied AI, integrations, customer-facing implementation, and ownership of systems beyond the first successful demo.
