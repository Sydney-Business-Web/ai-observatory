# AI Observatory — Technical Architecture

AI Observatory is a retrieval-monitoring and evidence system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/).

Its purpose is to observe, classify and report qualified retrieval activity from recognised AI and search crawler systems.

This document describes the high-level production architecture. Proprietary source code, qualification algorithms and detailed filtering rules are intentionally excluded.

## Architectural Principle

AI Observatory separates three functions:

1. **Observation** — detect relevant requests at the network edge.
2. **Qualification** — determine whether an observed request meets the criteria for reportable retrieval evidence.
3. **Reporting** — present qualified measurements independently of the website being monitored.

This separation is important because the presence of a crawler User-Agent alone is not treated as sufficient evidence.

## High-Level Architecture

The production architecture is based on Cloudflare edge infrastructure.

The processing flow can be represented as:

**Incoming request**  
→ **Cloudflare edge**  
→ **Worker telemetry layer**  
→ **crawler/request classification**  
→ **qualification and filtering**  
→ **Analytics Engine storage**  
→ **reporting Worker**  
→ **AI Observatory evidence interface**

The monitored WordPress website is not responsible for generating the underlying retrieval evidence.

## 1. Edge Telemetry

Relevant request information is observed at the Cloudflare edge using Cloudflare Workers.

This allows retrieval activity to be examined before dependence on WordPress application logging or conventional server-log interpretation.

The telemetry layer records information required for subsequent classification and measurement.

## 2. Crawler and Request Classification

Observed traffic is evaluated to determine whether it is associated with recognised AI or search crawler activity.

Classification can include distinctions between:

- recognised crawler systems;
- requested resource types;
- business-content retrieval;
- discovery-related retrieval;
- successful and unsuccessful requests;
- diagnostic or test traffic.

Crawler recognition is only one stage of the process.

A claimed User-Agent string is not automatically treated as proof of qualified retrieval.

## 3. Qualification and Filtering

AI Observatory applies qualification rules before retrieval activity is included in reported evidence.

The purpose of this layer is to reduce false positives and prevent irrelevant or diagnostic activity from being presented as meaningful business retrieval.

The detailed qualification logic is proprietary to Sydney Business Web and is not published in this repository.

## 4. Telemetry Storage

Qualified telemetry is stored independently of the WordPress application using **Cloudflare Analytics Engine**.

Separating measurement storage from the monitored website provides a distinct telemetry layer for retrieval analysis.

## 5. Reporting Layer

A separate reporting Worker processes stored measurements and produces the data used by the AI Observatory reporting interface.

This maintains separation between:

- traffic observation;
- telemetry storage;
- qualification logic;
- public reporting.

The resulting interface can present measurements such as rolling retrieval summaries and crawler-specific retrieval activity.

## Systems Covered

AI Observatory is designed to observe relevant activity associated with recognised AI and search systems, including crawlers operated by organisations such as:

- Google
- Microsoft / Bing
- OpenAI
- Anthropic
- Perplexity
- Apple

The architecture can be extended as crawler ecosystems and AI retrieval systems evolve.

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

A successful qualified retrieval establishes that the relevant system accessed a resource under the Observatory's measurement criteria.

It does not establish what subsequently happened inside an external AI or search system.

## Why the Architecture Is Separated

A conventional bot counter may simply count requests matching particular User-Agent strings.

AI Observatory is designed differently.

Its architecture separates edge observation, classification, qualification, storage and reporting so that reported retrieval evidence is the output of a measurement process rather than a raw request count.

This distinction is central to the design of the system.

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

Cloudflare crawler-monitoring architecture:  
https://sydneybusinessweb.com.au/ai-crawler-monitoring-cloudflare-edge/

Sydney Business Web:  
https://sydneybusinessweb.com.au/

---

**AI Observatory is proprietary technology developed by Sydney Business Web.**

This repository documents architectural principles and terminology for technical reference. Production source code and proprietary qualification logic are not distributed here.

© Sydney Business Web. All rights reserved.
