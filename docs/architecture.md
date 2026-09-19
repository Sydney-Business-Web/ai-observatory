# AI Observatory — Technical Architecture

AI Observatory is a retrieval-monitoring and evidence system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/).

Its purpose is to observe, qualify and report retrieval activity from recognised AI and search crawler systems.

This document describes the high-level production architecture. Proprietary source code, private thresholds and detailed implementation logic are intentionally excluded.

## Current Architecture Version

The current public technical documentation is **v1.1.0**, aligned with **Measurement Contract 1.4**, finalised on 20 September 2026.

The principal architectural change from the initial documentation is the formal separation of a reusable Observatory measurement core from the telemetry adapter used by a particular hosting environment.

## Architectural Principle

AI Observatory separates four functions:

1. **Observation** — obtain relevant request and response evidence from the monitored environment.
2. **Attribution and qualification** — establish site attribution, crawler identity and measurement eligibility.
3. **Scoring** — apply the shared retrieval-outcome rules to current qualified resources.
4. **Reporting** — present qualified measurements independently of the website application.

This separation is important because the presence of a crawler User-Agent alone is not treated as sufficient evidence, and because the same measurement contract can be supported by different telemetry sources.

## Observatory Core and Telemetry Adapters

AI Observatory is designed around a common measurement core with environment-specific telemetry adapters.

The shared core governs principles including:

- crawler identity qualification;
- autonomous versus user-requested activity;
- current business-resource qualification;
- machine-discovery qualification;
- retrieval-outcome scoring;
- rolling reporting windows;
- public measurement boundaries.

The telemetry adapter supplies the evidence required by that core.

Two production patterns currently demonstrate the approach:

### Cloudflare Edge Adapter

A Cloudflare-based implementation can observe relevant request and response information at the website edge.

A typical flow is:

**Incoming request**  
→ **Cloudflare edge**  
→ **Worker telemetry layer**  
→ **Analytics Engine storage**  
→ **reporting Worker**  
→ **AI Observatory evidence interface**

### Apache / cPanel Server-Log Adapter

A shared-hosting implementation can use attributable Apache/cPanel access-log evidence where direct edge telemetry is not available.

A typical flow is:

**Website request**  
→ **Apache/cPanel domain or account log**  
→ **collector and evidence qualification**  
→ **D1 event storage**  
→ **reporting Worker**  
→ **AI Observatory evidence interface**

The adapter can differ while the public retrieval-scoring contract remains the same.

## 1. Observation

Relevant request and response information is obtained from the production environment.

Depending on the deployment, this can occur at the network edge or through sufficiently attributable server-log evidence.

The observation layer records the information required for subsequent attribution, qualification and scoring.

## 2. Site Attribution

Before an observation can contribute to a site-specific score, the system must establish a defensible basis for attributing it to the monitored site.

The strongest available attribution evidence depends on the telemetry environment.

For an edge deployment, the target site can be known directly from the request context.

For a server-log deployment, account- or domain-specific log provenance can provide site attribution even where exact requested-host resolution is unavailable.

The governing design rule is:

> **Site attribution precedes site scoring.**

## 3. Crawler Identity and Request Qualification

Observed traffic is evaluated to determine whether it is associated with recognised AI or search crawler activity and whether the identity meets the public corroboration threshold.

Qualification can include distinctions between:

- sufficiently corroborated crawler systems;
- autonomous crawler behaviour;
- user-requested retrieval;
- diagnostic or test traffic;
- current business resources;
- approved machine-discovery resources;
- response outcomes.

A claimed User-Agent string is not automatically treated as proof of qualified retrieval.

## 4. Current Resource Registries

Measurement Contract 1.4 uses explicit current-resource qualification.

Each deployment maintains an approved registry of current business resources that are eligible for business-retrieval scoring.

Machine-discovery resources are maintained separately through an explicit discovery whitelist.

Unknown, stale, internal, support and other unqualified paths do not enter the business-retrieval denominator.

This prevents historical or irrelevant URLs from distorting the current retrieval-success measurement.

## 5. Retrieval Outcome Scoring

For qualifying GET requests:

- **2xx** responses count as successful retrievals;
- **4xx and 5xx** responses count as failed retrievals;
- **3xx** responses are retained as evidence but treated as neutral and excluded from success-rate denominators.

Business and discovery outcomes are scored separately.

A redirect response is not treated as a failed retrieval, and the Observatory does not infer that a crawler followed the redirect unless a subsequent request is independently observed.

## 6. Telemetry Storage

Storage is kept separate from the monitored website application.

Current deployments use services appropriate to their telemetry source, including **Cloudflare Analytics Engine** and **Cloudflare D1**.

The storage layer preserves the evidence required for reporting while allowing the monitored WordPress website to remain separate from the measurement system.

## 7. Reporting Layer

A separate reporting Worker applies the public measurement rules and produces the data used by the Observatory evidence interface.

This maintains separation between:

- traffic observation;
- site attribution;
- identity qualification;
- resource qualification;
- telemetry storage;
- retrieval scoring;
- public reporting.

The resulting interface can present rolling retrieval summaries and crawler-specific retrieval activity without exposing proprietary production code.

## Systems Covered

AI Observatory is designed to observe relevant activity associated with recognised AI and search systems, including crawlers operated by organisations such as:

- Google
- Microsoft / Bing
- OpenAI
- Anthropic
- Perplexity
- Apple

The architecture can be extended as crawler ecosystems and AI retrieval systems evolve.

A newly encountered crawler is not automatically promoted into headline measurement merely because it identifies itself with a new User-Agent. Identity and corroboration rules are added deliberately before it can contribute to the scored evidence.

## Measurement Boundary

AI Observatory measures **observable retrieval activity**.

It does not claim that retrieval proves:

- model training;
- model memory;
- semantic understanding;
- recommendation;
- ranking;
- citation;
- endorsement.

A successful qualified retrieval establishes that the relevant system accessed a current eligible resource under the Observatory's measurement criteria.

It does not establish what subsequently happened inside an external AI or search system.

## Why the Architecture Is Separated

A conventional bot counter may simply count requests matching particular User-Agent strings.

AI Observatory is designed differently.

Its architecture separates observation, attribution, qualification, scoring, storage and reporting so that reported retrieval evidence is the output of a defined measurement process rather than a raw request count.

The adapter/core separation also allows the same measurement logic to be used across different hosting environments without pretending that all telemetry sources are identical.

## Relationship to AI Visibility

Retrieval is one layer of AI Visibility.

AI Observatory provides evidence about whether machines are retrieving website resources.

Sydney Business Web's **Schema Gorilla** addresses a different question: whether the information and entity relationships exposed by the website form a coherent machine-readable representation of the business.

Together, these support analysis across:

**retrieval → machine-readable identity → AI Visibility assessment**

## Further Information

AI Observatory overview:  
https://sydneybusinessweb.com.au/ai-observatory-verified-ai-retrieval-monitoring/

AI Retrieval Evidence:  
https://sydneybusinessweb.com.au/ai-retrieval-evidence/

Retrieval methodology:  
https://github.com/Sydney-Business-Web/ai-observatory/blob/main/docs/retrieval-methodology.md

Measurement boundary:  
https://github.com/Sydney-Business-Web/ai-observatory/blob/main/docs/measurement-boundary.md

Sydney Business Web:  
https://sydneybusinessweb.com.au/

---

**AI Observatory is proprietary technology developed by Sydney Business Web.**

This repository documents architectural principles and terminology for technical reference. Production source code, private thresholds and proprietary implementation logic are not distributed here.

© Sydney Business Web. All rights reserved.
