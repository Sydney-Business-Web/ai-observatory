# AI Observatory

**AI Observatory** is a technical retrieval-monitoring system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/) for measuring and qualifying access to websites by recognised AI and search crawler systems.

It is designed to answer a specific question:

> **Are AI and search systems actually retrieving the website, and what are they retrieving?**

AI Observatory is not simply a bot counter or conventional server-log viewer. It uses qualified telemetry, site attribution, crawler corroboration, current-resource qualification and retrieval-outcome rules to produce defensible evidence of machine access to web resources.

## Current Documentation Version

**Technical documentation:** v1.1.0  
**Measurement Contract:** 1.4  
**Finalised:** 20 September 2026

Version 1.1.0 formalises:

- site attribution before site-specific scoring;
- corroborated crawler identity rather than User-Agent counting alone;
- separation of autonomous crawling from owner-triggered diagnostics and user-requested retrieval;
- explicit current business-resource registries;
- separate machine-discovery measurement;
- 2xx success, 4xx/5xx failure and neutral 3xx redirect treatment;
- adapter-independent measurement across different hosting and telemetry environments.

The production source code and proprietary implementation remain private.

## DOI

AI Observatory documentation v1.1.0 is archived on Zenodo:

**DOI:** [10.5281/zenodo.22850808](https://doi.org/10.5281/zenodo.22850808)

Previous release:

- v1.0.0 — [10.5281/zenodo.22040578](https://doi.org/10.5281/zenodo.22040578)

## Developed By

**Sydney Business Web**  
Thornton, NSW, Australia

Technical architecture and development: **Keith Rowley — Co-Owner & Lead Engineer**

Official website:  
https://sydneybusinessweb.com.au/

AI Observatory overview:  
https://sydneybusinessweb.com.au/ai-observatory-verified-ai-retrieval-monitoring/

AI Retrieval Evidence:  
https://sydneybusinessweb.com.au/ai-retrieval-evidence/

Technical crawler-monitoring architecture:  
https://sydneybusinessweb.com.au/ai-crawler-monitoring-cloudflare-edge/

## Purpose

Modern AI visibility cannot be assessed reliably by assuming that a crawler has accessed a website merely because a User-Agent string appears in a log.

AI Observatory was developed to provide a more rigorous measurement layer for AI Visibility engineering.

The system is designed to distinguish between:

- recognised and sufficiently corroborated AI and search crawler activity;
- autonomous and user-requested retrieval;
- successful and unsuccessful retrievals;
- current business-resource retrieval and machine-discovery activity;
- diagnostic or controlled test traffic;
- traffic and resource requests that do not meet the system's qualification requirements.

The resulting measurements provide evidence of **retrieval**, rather than assumptions about crawler behaviour.

## Architecture

AI Observatory uses a shared measurement core with environment-specific telemetry adapters.

The common measurement layer governs:

1. **Observation** of production request and response evidence.
2. **Site attribution** before site-specific scoring.
3. **Crawler identity qualification** and corroboration.
4. **Autonomous-activity qualification.**
5. **Current business-resource qualification.**
6. **Separate machine-discovery qualification.**
7. **Retrieval-outcome scoring.**
8. **Independent public reporting.**

Current production implementations demonstrate two telemetry patterns:

- **Cloudflare edge telemetry**, with Analytics Engine and a reporting Worker.
- **Apache/cPanel server-log telemetry**, with collector processing, D1 storage and a reporting Worker.

The evidence source can differ while the public measurement contract remains the same.

## Measurement Contract 1.4

For qualifying GET requests to current approved resources:

- **2xx** responses count as successful retrievals;
- **4xx and 5xx** responses count as failed retrievals;
- **3xx** responses are retained as evidence but are neutral and excluded from success-rate denominators.

Business retrieval and machine discovery are scored separately.

Business-retrieval scoring is restricted to an explicit registry of current approved business resources. Stale URLs, legacy paths, support assets, internal paths and otherwise unqualified resources do not enter the business-retrieval denominator.

Machine-discovery scoring uses a separate explicit whitelist of approved machine-facing discovery resources.

A redirect is not treated as a failed retrieval, and AI Observatory does not infer that a crawler followed a redirect unless a subsequent request is independently observed.

## Systems Observed

AI Observatory can identify relevant retrieval activity associated with recognised systems including crawlers operated by organisations such as:

- Google
- Microsoft / Bing
- OpenAI
- Anthropic
- Perplexity
- Apple

Recognition of a crawler does **not** imply endorsement, recommendation or inclusion of the website in an AI-generated answer.

A newly encountered crawler is not automatically added to headline measurement simply because it presents a new User-Agent. Identity and corroboration rules are added deliberately before it can contribute to scored evidence.

## Measurement Boundary

AI Observatory has an explicit measurement boundary.

It measures observable website retrieval activity.

It does **not** claim that retrieval proves:

- model training;
- model memory;
- semantic understanding;
- recommendation;
- ranking;
- citation in an AI answer;
- commercial endorsement by an AI provider.

This distinction is fundamental to the system.

Retrieval evidence establishes that a sufficiently corroborated system accessed a qualifying resource under the Observatory's measurement criteria. Further AI Visibility analysis is required to determine whether a business is being understood, selected or cited by answer engines.

## Relationship to AI Visibility Engineering

AI Observatory forms part of Sydney Business Web's broader AI Visibility engineering methodology.

It complements systems such as **Schema Gorilla**, which evaluates whether the information and entity relationships exposed by a website provide machines with a coherent representation of the business.

In simplified terms:

**AI Observatory asks whether machines are retrieving the evidence.**

**Schema Gorilla examines whether the evidence forms a coherent machine-readable business identity.**

Together these address two different layers of AI Visibility:

**retrieval → understanding**

## Public Technical Documentation

The repository contains:

- [Technical architecture](docs/architecture.md)
- [Retrieval methodology](docs/retrieval-methodology.md)
- [Measurement boundary](docs/measurement-boundary.md)

These documents describe the public architecture and measurement principles without distributing the production implementation.

## Repository Scope

This repository provides public technical documentation relating to the architecture, terminology and measurement principles of AI Observatory.

The production source code, private thresholds, qualification algorithms, authentication mechanisms and commercial implementation remain proprietary to Sydney Business Web.

This repository should therefore not be interpreted as an open-source distribution of AI Observatory.

## Intellectual Property

AI Observatory is a proprietary system developed by Sydney Business Web.

The documentation in this repository is publicly available for technical reference and citation only.

Copyright © 2026 Sydney Business Web. All rights reserved.

No licence is granted to reproduce, modify, distribute, commercially exploit, or create derivative works from the documentation in this repository without prior written permission from Sydney Business Web, except where permitted by law.

The production implementation, proprietary source code, filtering logic, qualification algorithms, internal thresholds, authentication mechanisms and commercial implementation remain proprietary to Sydney Business Web and are not included in this repository.

This repository should not be interpreted as an open-source distribution of AI Observatory.

© Sydney Business Web. All rights reserved.
