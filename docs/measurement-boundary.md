# AI Observatory — Measurement Boundary

AI Observatory is a retrieval-monitoring and evidence system developed by [Sydney Business Web](https://sydneybusinessweb.com.au/).

This document defines the boundary between what AI Observatory can directly measure and what cannot legitimately be inferred from retrieval telemetry alone.

## What AI Observatory Measures

AI Observatory measures observable website retrieval activity that satisfies its defined qualification criteria.

This can include evidence that a recognised AI or search crawler:

- requested a website resource;
- successfully or unsuccessfully retrieved that resource;
- retrieved substantive business content;
- performed discovery-related activity;
- accessed particular classes of website resources;
- changed its retrieval behaviour over time.

These are observable events occurring at the website or network edge.

## What Retrieval Evidence Establishes

A qualified retrieval establishes a deliberately limited fact:

> **A recognised external system accessed a particular web resource under the Observatory's measurement criteria.**

This provides useful evidence for the retrieval layer of AI Visibility.

It does not establish what subsequently occurred inside the external system.

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

This document defines the public measurement boundary. Production qualification logic and proprietary implementation details are not distributed here.

© Sydney Business Web. All rights reserved.
