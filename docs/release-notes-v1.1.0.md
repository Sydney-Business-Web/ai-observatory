# AI Observatory — Documentation Release v1.1.0

**Release date:** 20 September 2026  
**Measurement Contract:** 1.4  
**Publisher:** Sydney Business Web

## Purpose of this release

Version 1.1.0 updates the public technical documentation for AI Observatory to reflect Measurement Contract 1.4.

The release documents changes to the measurement model and architecture only. It does **not** publish production source code, private thresholds, credentials, deployment configuration or proprietary qualification logic.

## Measurement Contract 1.4

Contract 1.4 formalises the following public rules:

- site attribution precedes site-specific scoring;
- crawler identity must meet the public corroboration threshold;
- autonomous crawler activity is separated from owner-triggered diagnostics and user-requested retrieval;
- business retrieval is restricted to an explicit registry of current approved business resources;
- machine-discovery retrieval is measured separately through an explicit discovery whitelist;
- qualifying GET responses in the 2xx range count as successful retrievals;
- qualifying GET responses in the 4xx or 5xx range count as failed retrievals;
- 3xx responses are retained as evidence but treated as neutral and excluded from success-rate denominators;
- stale, unknown, internal, support and otherwise unqualified resources do not enter the business-retrieval score;
- a redirect response does not by itself establish that the crawler subsequently followed the redirect;
- where no scored attempts exist in a reporting window, a success rate is unavailable rather than zero.

## Architectural update

Version 1.1.0 also documents the separation between a common Observatory measurement core and environment-specific telemetry adapters.

The same public measurement contract can therefore be supported by different evidence sources, including:

- Cloudflare edge telemetry with Analytics Engine and a reporting Worker; and
- attributable Apache/cPanel server-log telemetry with collector processing, D1 storage and a reporting Worker.

The telemetry source can differ while the measurement contract remains common.

## Measurement boundary

The release preserves the existing conservative boundary:

AI Observatory measures observable retrieval evidence. It does not claim that retrieval proves model training, memory, semantic understanding, ranking, recommendation, citation or endorsement.

## Files updated

- `README.md`
- `docs/architecture.md`
- `docs/retrieval-methodology.md`
- `docs/measurement-boundary.md`

## Previous release

The initial public technical documentation release, v1.0.0, was published on 21 August 2026 and archived on Zenodo as DOI:

**10.5281/zenodo.22040578**

The v1.1.0 documentation release is archived on Zenodo as DOI:

**10.5281/zenodo.22850808**

---

**AI Observatory is proprietary technology developed by Sydney Business Web.**

This repository provides public technical documentation for reference and citation. Production source code and proprietary implementation details are not distributed here.

© 2026 Sydney Business Web. All rights reserved.
