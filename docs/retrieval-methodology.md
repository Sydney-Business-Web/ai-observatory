# AI Observatory — Retrieval Methodology

AI Observatory is a technical retrieval-monitoring system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/).

This document describes the public methodology used to distinguish observable crawler activity from retrieval evidence suitable for AI Visibility analysis.

Detailed production code, private thresholds and proprietary implementation logic are intentionally excluded.

## Current Measurement Contract

The current public measurement contract is **1.4**, finalised on 20 September 2026.

Measurement Contract 1.4 formalises several principles that are important to defensible retrieval measurement:

- site attribution is established before site-specific scoring;
- recognised crawler identity must meet the public corroboration threshold;
- autonomous activity is separated from owner-triggered diagnostics and user-requested retrieval;
- business retrieval is scored only against an explicit registry of current approved business resources;
- machine-discovery retrieval is measured separately against an explicit discovery-resource whitelist;
- qualifying GET responses in the 2xx range count as successful retrievals;
- qualifying GET responses in the 4xx or 5xx range count as failed retrievals;
- 3xx responses are retained as evidence but treated as neutral and excluded from success-rate denominators;
- stale, unknown, internal, support and otherwise unqualified resources fail closed and do not enter the business-retrieval score.

The same measurement contract can be implemented through different telemetry adapters, provided that the evidence source can support the required attribution and qualification rules.

## Retrieval as an Observable Event

AI Observatory starts from a deliberately narrow principle:

> A retrieval event is evidence that a recognised system accessed a website resource under defined measurement conditions.

Retrieval is observable.

What an external AI or search system subsequently does with the retrieved information is not directly observable from the website.

AI Observatory therefore separates **retrieval evidence** from claims about model behaviour.

## Why User-Agent Counting Is Insufficient

A conventional crawler report may count every request containing a recognised User-Agent string.

AI Observatory does not treat this alone as sufficient evidence.

Raw request counts can be affected by:

- diagnostic activity;
- controlled tests;
- user-requested retrieval;
- unsuccessful requests;
- redirects;
- stale or legacy URLs;
- support assets and internal paths;
- discovery activity;
- traffic that claims a crawler identity but does not satisfy qualification requirements.

For this reason, observation, attribution, qualification and scoring are separate stages.

## Site Attribution

Before an event can contribute to a site-specific retrieval score, the Observatory must have a defensible basis for attributing the observation to the monitored site.

The precise evidence source can vary by implementation. For example, one deployment may observe requests directly at the website edge, while another may use server-log provenance from a hosting account or domain-specific log.

The governing principle is:

> **Site attribution precedes site scoring.**

Exact requested-host resolution is useful where available, but it is not the only possible basis for attribution when the telemetry source itself provides sufficiently specific site provenance.

## Crawler Identity and Corroboration

Crawler recognition is not based on User-Agent text alone.

A claimed crawler identity must satisfy the Observatory's public corroboration threshold before it can contribute to headline autonomous measurements.

The supporting evidence available varies by provider and telemetry environment. Publicly documented provider network information can form part of corroboration where appropriate.

Traffic that merely claims a recognised crawler identity but cannot be sufficiently corroborated is not promoted into public headline evidence.

## Autonomous Retrieval

AI Observatory distinguishes autonomous crawler behaviour from activity initiated by a human or site operator.

Owner-triggered diagnostics, controlled Observatory tests and user-requested AI retrieval may be retained as telemetry, but they do not enter the autonomous headline measurements.

Examples of user-requested activity can include retrieval classes such as ChatGPT-User, Claude-User or Perplexity-User when the request represents a user-initiated fetch rather than independent crawler discovery.

This separation prevents controlled or user-triggered activity from artificially increasing autonomous retrieval counts.

## Current Business-Resource Qualification

Under Measurement Contract 1.4, business retrieval is not inferred from whether an error response happens to look like HTML, nor from a broad content-type classification alone.

A request can enter the business-retrieval score only when its path qualifies against the deployment's explicit registry of **current approved business resources**.

The registry can include current public pages and documents that the monitored organisation has determined belong to the business-information surface being measured.

Resources outside that registry — including stale URLs, legacy paths, support assets, internal paths and unrecognised resources — do not enter the business-retrieval score.

This approach makes the denominator explicit and prevents obsolete or irrelevant requests from distorting the public retrieval-success rate.

## Machine-Discovery Qualification

Machine discovery is measured separately from business-information retrieval.

A deployment maintains an explicit whitelist of current machine-facing discovery resources, such as the site's recognised robots, llms and sitemap entry points.

Discovery outcomes are reported independently and do not alter the business-retrieval success percentage.

This distinction answers two different questions:

**Business retrieval:** Can the machine successfully fetch current business information?

**Machine discovery:** Can the machine successfully fetch the resources intended to help it discover or navigate the site?

## Retrieval Outcomes

For a qualifying GET request under Measurement Contract 1.4:

- **2xx** — successful retrieval;
- **4xx or 5xx** — failed retrieval;
- **3xx** — neutral redirect, retained as evidence but excluded from the success-rate denominator.

A redirect is therefore not treated as a failed retrieval merely because the first response is not 2xx.

The Observatory also does not infer from a redirect response alone that a crawler subsequently followed the redirect.

## Business Retrieval Success Rate

The public business retrieval success rate is calculated from qualifying current business-resource requests that produced a terminal success or failure outcome:

**successful qualifying 2xx business retrievals ÷ qualifying 2xx, 4xx and 5xx business retrievals**

3xx responses remain observable evidence but are not included in this denominator.

If there are no scored attempts in the reporting window, the rate is reported as unavailable rather than as 0%.

## Evidence Aggregation

Qualified retrieval events can be aggregated into reporting periods such as rolling 24-hour summaries.

Aggregation can provide evidence including:

- number of qualifying autonomous machine systems observed;
- successful business-information retrievals;
- business retrieval success rate;
- machine-discovery retrievals;
- crawler-specific activity;
- changes in retrieval behaviour over time.

The reporting layer can cache a generated snapshot for a defined interval. Repeated requests within that interval can therefore legitimately return the same generated timestamp.

The purpose is not to maximise a bot count.

The purpose is to make changes in meaningful machine retrieval observable.

## Measurement Boundary

AI Observatory reports what can be supported by observable retrieval evidence.

A qualified retrieval does **not** establish that the external system:

- trained a model on the content;
- stored the content in model memory;
- understood the business correctly;
- incorporated the information into a knowledge representation;
- ranked the business;
- recommended the business;
- cited the business in an answer;
- endorsed the business.

Those are separate questions requiring separate evidence.

## Retrieval and AI Visibility

Retrieval is nevertheless a necessary technical layer of AI Visibility.

If an AI or search system cannot retrieve relevant business information, it has reduced opportunity to use that information when constructing search or answer experiences.

AI Observatory therefore provides evidence for the retrieval layer:

**Can the machine access the evidence?**

Other analysis is required for subsequent layers, including:

**Does the available information form a coherent business identity?**

and ultimately:

**Is the business being selected, represented or cited in AI-generated answers?**

Sydney Business Web uses AI Observatory alongside systems such as **Schema Gorilla** to investigate these different layers independently.

## Methodological Principle

The central methodological principle of AI Observatory is:

> **Measure what is observable and do not claim what the evidence cannot establish.**

This boundary is intended to make retrieval measurements technically useful and defensible.

## Further Information

AI Observatory:  
https://sydneybusinessweb.com.au/ai-observatory-verified-ai-retrieval-monitoring/

AI Retrieval Evidence:  
https://sydneybusinessweb.com.au/ai-retrieval-evidence/

Technical architecture:  
https://github.com/Sydney-Business-Web/ai-observatory/blob/main/docs/architecture.md

Measurement boundary:  
https://github.com/Sydney-Business-Web/ai-observatory/blob/main/docs/measurement-boundary.md

Sydney Business Web:  
https://sydneybusinessweb.com.au/

---

**AI Observatory is proprietary technology developed by Sydney Business Web.**

This document describes the public methodology and measurement principles. Production source code, private thresholds and proprietary implementation logic are not distributed here.

© Sydney Business Web. All rights reserved.
