# AI Observatory

**AI Observatory** is a technical retrieval-monitoring system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/) for measuring and qualifying access to websites by recognised AI and search crawler systems.

It is designed to answer a specific question:

> **Are AI and search systems actually retrieving the website, and what are they retrieving?**

AI Observatory is not simply a bot counter or conventional server-log viewer. It uses edge telemetry, retrieval classification and qualification rules to produce defensible evidence of machine access to web resources.

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

- recognised AI and search crawler activity;
- successful and unsuccessful retrievals;
- business-content retrieval and discovery activity;
- resource types being requested;
- diagnostic or test traffic;
- traffic that does not meet the system's qualification requirements.

The resulting measurements provide evidence of **retrieval**, rather than assumptions about crawler behaviour.

## Architecture

The production implementation uses Cloudflare edge infrastructure to observe and classify relevant requests before reporting qualified retrieval evidence.

The architecture includes:

1. **Edge telemetry collection** using Cloudflare Workers.
2. **Crawler and request classification** at the edge.
3. **Filtering and qualification rules** to reduce false-positive evidence.
4. **Retrieval-state and resource-type classification.**
5. **Telemetry storage** using Cloudflare Analytics Engine.
6. **Independent reporting logic** for producing qualified retrieval measurements.
7. **Rolling retrieval summaries** for recognised AI and search systems.

The telemetry and reporting layers are deliberately separated from the WordPress website being measured.

## Systems Observed

AI Observatory can identify relevant retrieval activity associated with recognised systems including crawlers operated by organisations such as:

- Google
- Microsoft / Bing
- OpenAI
- Anthropic
- Perplexity
- Apple

Recognition of a crawler does **not** imply endorsement, recommendation or inclusion of the website in an AI-generated answer.

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

Retrieval evidence establishes that a recognised system accessed a resource. Further AI Visibility analysis is required to determine whether a business is being understood, selected or cited by answer engines.

## Relationship to AI Visibility Engineering

AI Observatory forms part of Sydney Business Web's broader AI Visibility engineering methodology.

It complements systems such as **Schema Gorilla**, which evaluates whether the information and entity relationships exposed by a website provide machines with a coherent representation of the business.

In simplified terms:

**AI Observatory asks whether machines are retrieving the evidence.**

**Schema Gorilla examines whether the evidence forms a coherent machine-readable business identity.**

Together these address two different layers of AI Visibility:

**retrieval → understanding**

## Repository Scope

This repository provides public technical documentation relating to the architecture, terminology and measurement principles of AI Observatory.

The production source code, filtering logic, qualification algorithms and commercial implementation remain proprietary to Sydney Business Web.

This repository should therefore not be interpreted as an open-source distribution of AI Observatory.

## Intellectual Property

AI Observatory is a proprietary system developed by Sydney Business Web.

Documentation in this repository is provided for technical reference and transparency. No licence to reproduce the proprietary implementation, algorithms or commercial system is granted unless explicitly stated.

© Sydney Business Web. All rights reserved.
