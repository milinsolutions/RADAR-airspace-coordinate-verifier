# RADAR — Rapid Area Definition Access for Romania

**Zero-dependency browser-based coordinate verification and retrieval tool for Romanian airspace NOTAMs**

---

## Overview
RADAR is a lightweight, browser-native operational safety tool that eliminates manual coordinate transcription errors in flight planning operations. Built as a single HTML file requiring zero installation, it serves as a verified single source of truth for Romanian airspace restriction coordinates — accessible instantly from any shared terminal or browser environment.

---

## Executive Summary
Developed to address a daily operational safety risk where analysts manually transcribed complex polygon coordinates from a 200-page PDF manual into a flight planning system under time pressure. RADAR replaces this error-prone process with instant verified retrieval and one-click clipboard delivery, reducing processing time from approximately 3 minutes to 5 seconds per NOTAM while eliminating the need for manual coordinate transcription.

---

## The Problem
Every day between 12:00 and 13:00 UTC, the NOTAM team receives a bulk influx of 50–60 complex Romanian airspace restriction NOTAMs — LRTRA, LRD, and LRTSA areas. These NOTAMs reference area names only, omitting the geographic coordinates required for flight planning rule creation.

This forced a slow and safety-critical manual process:

- **Manual lookup:** Analyst searches through a dense 200-page PDF to locate the specific area
- **Manual transcription:** Complex polygon coordinates — often 10–15 points per area — typed manually into the flight planning system
- **Safety risk:** A single transcription error can create an inaccurate airspace definition, introducing critical operational risk into the flight planning workflow
- **Duplicated QC effort:** Quality checkers repeat the identical PDF lookup to verify each entry, effectively doubling the workload per NOTAM
- **Time cost:** Approximately 3 minutes per NOTAM during the team's busiest operational window

---

## The Solution
RADAR provides a fast, searchable browser interface that replaces the PDF lookup entirely. Analysts type an area name, instantly see the verified coordinates, and copy them to clipboard with one click — formatted exactly as required by the flight planning system, ready to paste without modification.

A built-in QC verification engine allows reviewers to paste coordinates directly from the flight planning system and receives an instant "Green Approved" or "Red Discrepancy" result, eliminating the need to repeat the manual PDF lookup for quality checking.

---

## Architecture
Single-file architecture intentionally chosen to maximize portability, simplify deployment, and eliminate runtime dependencies across shared operational workstations supporting time-critical aviation operations. All logic, data, and UI contained within one HTML file with zero external dependencies. Deployed on a shared terminal server accessible from any browser without installation, configuration, or IT involvement.

**Analyst flow:**
Analyst types area name → Intelligent search filters and highlights matches → Analyst selects area → Coordinates displayed and copied to clipboard → Paste directly into flight planning system

**QC flow:**
Reviewer copies coordinates from flight planning system → Pastes into RADAR verification engine → Bidirectional text matching with whitespace normalization → Instant Green Approved or Red Discrepancy result

---

## Features

- **Zero dependencies** — pure HTML, CSS, and JavaScript, no frameworks, no installation required
- **Intelligent search** — visual character highlighting and auto-expand as you type, collapsing irrelevant sections automatically
- **One-click clipboard delivery** — coordinates copied in exact flight planning system format, ready to paste without modification
- **Bidirectional QC verification** — cross-references pasted text against master data in both directions, handling partial pastes and whitespace variations gracefully
- **AIRAC cycle versioning** — tracks version and effective date, updatable every 28 days aligned with AIRAC publication cycle
- **Multi-part area support** — handles split altitude band areas as single searchable entries
- **Clipboard API with graceful fallback** — clear user instruction displayed if browser permissions are restricted
- **No server required** — runs entirely in the browser, works offline, deployable via simple file share

---

## Technical Stack

- **Core:** HTML5, CSS3, Vanilla JavaScript
- **Browser APIs:** Clipboard API
- **Deployment:** Single file, shared terminal server
- **Data:** Coordinates sourced from public Romanian AIP, updated every AIRAC cycle

---

## AI-Assisted Development

This project was developed using AI-assisted engineering practices to accelerate implementation, documentation, debugging, and iterative refinement.

AI served as an engineering accelerator throughout development, while architectural decisions, workflow design, operational validation, testing, and final implementation decisions remained under human review and responsibility.

This reflects my approach to modern engineering: combining domain expertise with AI to rapidly deliver practical, reliable operational solutions.

---

## Business Impact

| Metric | Before RADAR | After RADAR |
| --- | --- | --- |
| Processing time per NOTAM | ~3 minutes | ~5 seconds |
| Manual coordinate transcription | Eliminated |
| QC workload | Full duplicate PDF lookup | Instant paste verification |
| Daily NOTAM volume affected | 50–60 NOTAMs/day | 50–60 NOTAMs/day |
| Staff dependency | Individual PDF lookup | Centrally maintained verified database |
| Deployment | Manual PDF distribution | Instant (single HTML file) |
| Installation | PDF reader required | None |

**Operational window protected:** 12:00–13:00 UTC daily — the team's highest-volume, highest-pressure operational hour.

---

## Engineering Principles

RADAR was designed around operational simplicity and zero-friction adoption.

Core design principles include:

- Zero installation barrier — works from day one on any shared machine
- Single source of truth — all staff use identical verified coordinate data
- Domain-aware error handling — bidirectional matching accounts for real-world copy-paste behaviour
- AIRAC-aligned maintenance — update cycle matches regulatory publication rhythm
- Safety over convenience — verification engine designed to catch errors, not just display data
- Scalable framework — structure replicable for other complex airspace regions
- Human-centred design — optimized around real analyst workflows rather than technical elegance.

---

## Current Status

Operational. In active daily use by the NOTAM team during Romanian airspace restriction processing windows. Data maintained and updated every AIRAC cycle (28 days) against the published Romanian AIP.

---

## Future Roadmap

Planned enhancements include:

- Coverage expansion to additional complex airspace regions beyond Romania
- Automated AIRAC data validation against published AIP updates
- Adaptation for Enroute and Charts team workflows
- Web-hosted version with centralized data management

---

## Lessons Learned

The most effective tools are often the simplest ones. RADAR required no server, no framework, no database, and no IT department involvement — yet it eliminated a genuine daily safety risk and halved QC workload. Choosing zero-dependency architecture was not a limitation but a deliberate design decision that made deployment instant and adoption frictionless. Domain expertise was the critical ingredient — understanding exactly how analysts work under time pressure during the 12:00–13:00 UTC window shaped every design decision from search behaviour to clipboard formatting.

This project reinforced that operational improvements are not always driven by larger systems or more technology. Carefully observing repetitive workflows, understanding user behaviour, and removing friction at the right point can deliver disproportionate operational value. The best engineering solutions are often those that become almost invisible to the people who rely on them.

---

*Part of the **[Milin Solutions](https://milinsolutions.com)** portfolio.*