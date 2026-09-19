# AI Observatory — Measurement Boundary

AI Observatory is a retrieval-monitoring and evidence system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/).

This document defines the boundary between what AI Observatory can directly measure and what cannot legitimately be inferred from retrieval telemetry alone.

## Current Measurement Contract

The current public measurement contract is **1.4**, finalised on 20 September 2026.

Contract 1.4 formalises the distinction between:

- site attribution and site scoring;
- autonomous crawler behaviour and user-requested or owner-triggered retrieval;
- current business-resource retrieval and machine-discovery retrieval;
- successful, failed and neutral redirect outcomes.

These distinctions narrow the public evidence set deliberately.

## What AI Observatory Measures

AI Observatory measures observable website retrieval activity that satisfies its defined qualification criteria.

This can include evidence that a sufficiently corroborated AI or search crawler:

- requested a current approved business resource;
- successfully or unsuccessfully retrieved that resource;
- requested an approved machine-discovery resource;
- produced a 2xx, 3xx, 4xx or 5xx response outcome;
- changed its retrieval behaviour over time.

These are observable events occurring at the website edge or within another sufficiently attributable telemetry source.

## What Retrieval Evidence Establishes

A qualified retrieval establishes a deliberately limited fact:

> **A sufficiently corroborated external system accessed a qualifying web resource under the Observatory's measurement criteria.**

This provides useful evidence for the retrieval layer of AI Visibility.

It does not establish what subsequently occurred inside the external system.

## Site Attribution Boundary

A site-specific score is only meaningful when the underlying observation can first be attributed to the monitored site.

The telemetry source can differ between deployments. Direct edge observation, domain-specific access logs or account-specific server-log provenance can all provide attribution if they meet the deployment's evidence requirements.

The governing principle is:

> **Site attribution precedes site scoring.**

Where exact requested-host resolution is unavailable, AI Observatory does not automatically discard the observation if the telemetry source itself provides a defensible site-specific provenance.

## Identity Boundary

A crawler name in a User-Agent string is not, by itself, sufficient for headline evidence.

The claimed identity must meet the Observatory's public corroboration threshold.

Where the available evidence is insufficient, the observation can remain in private telemetry but is not promoted into the public autonomous measurements.

## Autonomous Activity Boundary

AI Observatory distinguishes autonomous crawler behaviour from activity initiated by a person or site operator.

Owner-triggered diagnostics, Observatory tests and user-requested AI retrieval may be retained as evidence, but they do not enter the autonomous headline measurements.

The purpose is to avoid presenting controlled or user-triggered retrieval as if it were independent crawler discovery.

## Current Resource Boundary

Business-retrieval scoring is restricted to an explicit registry of current approved business resources.

A request for a stale URL, legacy path, support asset, internal path or otherwise unqualified resource does not enter the business-retrieval denominator merely because it returned HTML or another content type.

Machine-discovery resources are maintained separately through an explicit discovery whitelist.

This means the public score describes retrieval of the **current qualified resource surface**, not every historical or guessed URL a crawler might request.

## Response Outcome Boundary

For a qualifying GET request:

- **2xx** is counted as a successful retrieval;
- **4xx or 5xx** is counted as a failed retrieval;
- **3xx** is retained as evidence but treated as neutral and excluded from the success-rate denominator.

A redirect response therefore does not count as a failure.

AI Observatory also does not infer that a crawler followed a redirect unless a later request is independently observed.

## What AI Observatory Does Not Claim

AI Observatory does not claim that retrieval proves:

- that website content was used for model training;
- that content entered model memory;
- that an AI system formed a particular semantic understanding;
- that the business was added to an internal knowledge representation;
- that the business achieved a particular ranking;
- that the business will be recommended;
- that the business will be cited in an AI-generated answer;
- that an AI provider endorses the business or Sydney Business Web.

These outcomes require different evidence.

## Retrieval Is Not Recommendation

A crawler accessing a page and an AI system recommending a business are separate events.

Retrieval may provide an external system with access to information, but the Observatory cannot observe the internal processes that determine whether that information is subsequently:

- retained;
- interpreted;
- weighted;
- combined with other sources;
- selected for an answer;
- ignored.

For this reason, AI Observatory deliberately avoids converting retrieval measurements into unsupported claims about AI recommendation.

## Recognition Is Not Verification by Association

Identification of traffic associated with organisations such as Google, Microsoft, OpenAI, Anthropic, Perplexity or Apple does not imply that those organisations:

- certify AI Observatory;
- approve its methodology;
- endorse Sydney Business Web;
- endorse a monitored website.

The names of external systems are used only to identify relevant observed crawler activity.

## Why the Boundary Matters

AI Visibility is vulnerable to exaggerated claims because much of the processing performed by external AI systems is not observable from a website.

AI Observatory therefore follows a conservative measurement principle:

> **Report what the evidence demonstrates, and stop where the evidence stops.**

This makes retrieval telemetry useful without presenting it as proof of outcomes that cannot be directly measured.

## Relationship to Other Evidence

Retrieval evidence is one component of a broader AI Visibility assessment.

Other evidence may separately examine:

- machine-readable business identity;
- entity relationships;
- structured data;
- external corroboration;
- search-engine representation;
- AI-generated answers;
- citations and recommendations.

Sydney Business Web uses **Schema Gorilla** to examine the coherence of the machine-readable business identity exposed by a website.

AI Observatory and Schema Gorilla therefore address different questions:

**AI Observatory:** Are machines retrieving the evidence?

**Schema Gorilla:** Does the available evidence form a coherent machine-readable representation of the business?

Neither system alone proves that an external AI will recommend the business.

## Methodological Position

The AI Observatory measurement boundary can be summarised as:

**observable retrieval → qualified evidence → defensible reporting**

not:

**retrieval → assumed understanding → assumed recommendation**

Maintaining that distinction is a core design principle of AI Observatory.

## Further Information

AI Observatory:  
https://sydneybusinessweb.com.au/ai-observatory-verified-ai-retrieval-monitoring/

AI Retrieval Evidence:  
https://sydneybusinessweb.com.au/ai-retrieval-evidence/

Retrieval methodology:  
https://github.com/Sydney-Business-Web/ai-observatory/blob/main/docs/retrieval-methodology.md

Technical architecture:  
https://github.com/Sydney-Business-Web/ai-observatory/blob/main/docs/architecture.md

Sydney Business Web:  
https://sydneybusinessweb.com.au/

---

**AI Observatory is proprietary technology developed by Sydney Business Web.**

This document defines the public measurement boundary. Production source code, private thresholds and proprietary implementation details are not distributed here.

© Sydney Business Web. All rights reserved.
