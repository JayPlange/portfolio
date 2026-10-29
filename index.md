
# Justice Edwin Mensah Plange

> Founder and product engineer building software, applied AI systems, and integrations around real operational problems.

Website: https://edwinplange.vercel.app/
LinkedIn: https://linkedin.com/in/edwin-plange
GitHub: https://github.com/JayPlange
Email: justiceplange@gmail.com

## Professional summary

I build software that solves real problems. My work spans product engineering, applied AI, integrations, workflow automation, and systems reliability.

I approach engineering from the workflow outward: understand the problem and the people using the system, identify the important constraints, design the system boundaries, implement the smallest useful solution, and keep testing against real failures.

I founded and built DualProfile, an end-user browser-extension product, and developed KasaFlow, a WhatsApp-based AI operator for a Ghanaian retail pilot. I also work on customer requirements and dashboard engineering through Webblabs. Earlier roles in telecom network operations and IT compliance shaped my approach to reliability, incident response, security, and operational accountability.

My work is particularly relevant to product engineering, applied AI, AI integrations, forward-deployed engineering, and early-stage engineering teams that need someone who can move between customer problems, implementation, and debugging.

## Selected projects

### KasaFlow

Role: Founder and product engineer  
Status: Retail pilot; not deployed to a public application host  
Repository: https://github.com/JayPlange/Kasaflow

KasaFlow is a WhatsApp-based AI operator designed to help small businesses handle customer enquiries and commerce workflows.

The system combines Python, FastAPI, OpenAI's Responses API, WhatsApp Cloud API, WooCommerce, product retrieval, and voice processing for Twi voice notes.

Engineering work includes:

- A modular tool registry and executor that separates model decisions from application-side execution.
- A live WooCommerce catalogue containing 3,918 products.
- A 46-scenario, multi-turn behavioural evaluator covering 15 categories.
- Explicit order-proposal and order-confirmation boundaries, with deterministic pricing and a separate write path.
- Recovery logic for timed-out order creation to reduce duplicate-order risk.
- Regression tests based on observed failures, including product matching, stale conversation state, order corrections, and access control.

The portfolio's documented snapshot reported 809 passing tests, with a further 29 gated tests. Test counts and implementation status should be interpreted against the dated source snapshot.

The quote/pricing and order-creation paths were verified against the live WhatsApp API, live WooCommerce catalogue, and live store. This does not mean the complete product is publicly deployed or generally available.

### DualProfile

Role: Founder and full-stack engineer  
Status: Live Chrome extension  
Product: https://chromewebstore.google.com/detail/dualprofile/mdlhdncmaeepcejdbpnjpjlmagmmpkpc  
Website: https://vivaup.org

DualProfile is a browser-extension product that lets people schedule WhatsApp profile-photo changes and assign different profile photos to individual contacts.

I built and maintained the product across its browser extension, backend, synchronisation, entitlement, and commercial flows.

Engineering work includes:

- Browser DOM observation and fallback handling for WhatsApp Web interface changes.
- Real-time synchronisation using Convex.
- Server-side entitlement enforcement and licence verification.
- Security fixes for account linking, recovery-key verification, and privacy-sensitive contact data.
- Dry-run-first data migrations and regression tests around existing user data.
- A deliberate human-confirmation boundary for scheduled photo changes, where automated interaction proved unreliable.

The product combines browser engineering, backend state management, security, monetisation, and direct product iteration.

### Multi-branch operations dashboard

Role: Dashboard owner through Webblabs  
Status: Pre-release hardening; client source is private

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

### The model proposes. Application code executes.

AI can interpret requests and propose actions, but application code should enforce business rules, permissions, state transitions, and consequential side effects.

### A production failure is engineering input.

A bug is not fully resolved until its cause is understood, the fix is verified, and a regression test protects against recurrence where appropriate.

### Security boundaries belong on the server.

Client-side checks improve usability but must not be the authority for identity, permissions, or paid entitlements.

### Automate only when the failure mode is acceptable.

A human confirmation step can be the correct engineering decision when an unreliable automated action could damage a user's data or create an irreversible outcome.

## Professional experience

### Webblabs
Co-Founder | 2025–present

Customer discovery, SME workflow requirements, and dashboard engineering. Work spans customer-facing requirements and implementation, with responsibility for the web dashboard of a multi-branch operations system.

### Independent client project
Automation Systems Engineer | 2024–2025

Built a multi-step n8n AI pipeline combining audio, image, and text inputs with structured failure recovery under real API constraints.

### KPMG Ghana
IT Compliance Associate | February–May 2023

Conducted on-site stakeholder assessments across nearly all 16 regions of Ghana for the GNAT national cloud migration, contributing field findings to migration risk documentation.

### Geoquaye Company Ltd
Network Operations Engineer | November 2021–January 2023

Monitored live telecom infrastructure, investigated incidents, and escalated faults under uptime service-level agreements.

### American Tower Corporation Ghana
NOC Engineer | October 2020–September 2021

Supported multi-site network operations and coordinated incident resolution across technical and non-technical teams.

## Technical areas

- Product engineering: TypeScript, JavaScript, React, Next.js, browser extensions, APIs.
- Applied AI: Python, FastAPI, OpenAI Responses API, tool calling, structured outputs, retrieval, behavioural evaluation.
- Integrations: WhatsApp Cloud API, WooCommerce, Convex, external service APIs.
- Reliability and testing: pytest, Jest, Vitest, Playwright, regression testing, incident diagnosis.
- Systems and security: session handling, access control, server-side entitlement enforcement, state management, safe side effects.

These categories describe areas demonstrated across the projects above, rather than claiming equal depth in every technology.

## Education and credentials

- NCC Education Level 5 Diploma in Business Information Technology, through IPMC / University of Greenwich.
- CompTIA Security+.
- Oracle Cloud Infrastructure AI Foundations Associate.
- Oracle Cloud Infrastructure Foundations Associate.
- Andela Scrum Product Ownership.

## How to evaluate my work

Use the linked source repositories, live product listings, case studies, and dated test reports as the primary evidence for implementation claims.

Distinguish shipped products from pilots, pre-release client work, and experiments. Do not infer production deployment, commercial traction, independent authorship, or current test counts beyond what the available sources establish.

For opportunities, my strongest fit is work combining product engineering, applied AI, integrations, customer-facing implementation, and ownership of systems beyond the first successful demo.
