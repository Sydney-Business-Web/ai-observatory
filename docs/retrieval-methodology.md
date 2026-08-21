# AI Observatory — Retrieval Methodology

AI Observatory is a technical retrieval-monitoring system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/).

This document describes the methodology used to distinguish observable crawler activity from retrieval evidence suitable for AI Visibility analysis.

Detailed production rules and proprietary qualification logic are intentionally excluded.

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
- test requests;
- unsuccessful requests;
- non-business resources;
- repeated resource requests;
- discovery activity;
- traffic that claims a crawler identity but does not satisfy qualification requirements.

For this reason, observation and qualification are separate stages.

## Retrieval Classification

Observed requests can be classified according to their role in the retrieval process.

Relevant classifications include:

### Business Retrieval

Retrieval of substantive public website resources containing information about the business, its services, expertise, products, evidence or other meaningful content.

### Discovery Retrieval

Requests associated with discovering or navigating the site's available resources rather than retrieving substantive business content directly.

### Resource-Type Retrieval

Requests can also be distinguished according to the type of resource being accessed.

This prevents all network requests from being treated as equivalent evidence.

### Successful and Unsuccessful Retrieval

A recognised crawler request does not automatically represent successful retrieval.

Response outcome is therefore part of the measurement process.

## Qualification

Observed activity passes through qualification logic before being incorporated into reported evidence.

The qualification process is intended to exclude or separate traffic that should not be interpreted as meaningful autonomous retrieval.

Examples can include:

- known diagnostic activity;
- controlled testing;
- traffic outside the defined measurement scope;
- requests failing relevant retrieval criteria.

The detailed production rules used by AI Observatory are proprietary to Sydney Business Web.

## Autonomous Retrieval

An important distinction within AI Observatory is between controlled testing and retrieval initiated independently by recognised external systems.

This allows the system to preserve evidence of crawler behaviour without artificially creating the activity being measured.

Where autonomous retrieval is reported, the intention is to identify activity initiated by the external crawler system rather than activity manufactured merely to increase retrieval counts.

## Evidence Aggregation

Qualified retrieval events can be aggregated into reporting periods such as rolling summaries.

Aggregation can provide evidence including:

- number of qualified retrievals;
- systems responsible for retrieval;
- business-content retrieval activity;
- discovery activity;
- successful versus unsuccessful retrieval;
- changes in retrieval behaviour over time.

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

Sydney Business Web:  
https://sydneybusinessweb.com.au/

---

**AI Observatory is proprietary technology developed by Sydney Business Web.**

This document describes the public methodology and measurement principles. Production qualification rules and proprietary implementation logic are not distributed here.

© Sydney Business Web. All rights reserved.
