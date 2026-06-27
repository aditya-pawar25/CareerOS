# ADR-002: Why CareerOS Uses a Career Knowledge Graph

**Project:** CareerOS
**Document ID:** COS-ADR-002
**Status:** Accepted
**Date:** 2026-06-27
**Decision Makers:** CareerOS Core Team

---

# Context

Career information is highly interconnected.

A single achievement may relate to:

* A company
* A project
* Multiple skills
* Business outcomes
* Technologies
* Leadership experiences
* Evidence collected during interviews

Traditional resume documents flatten these relationships into bullet points.

Relational databases can store the data, but complex relationships often require multiple joins and become increasingly difficult to manage as the model grows.

CareerOS requires a data model that represents relationships naturally and supports future AI reasoning.

---

# Problem

Most career platforms store information in isolated documents.

Typical structure:

Candidate

↓

Resume

↓

LinkedIn

↓

Cover Letter

↓

Interview Notes

Each document duplicates information.

Updating one document does not automatically update the others.

AI systems therefore receive fragmented context and often generate inconsistent outputs.

---

# Decision

CareerOS will organize career information around a **Career Knowledge Graph**.

The Knowledge Graph becomes the single source of truth for the platform.

Instead of storing disconnected documents, CareerOS stores structured entities and the relationships between them.

Examples include:

* Candidate
* Company
* Experience
* Project
* Achievement
* Skill
* Education
* Certification
* Evidence
* Job Description

Every output is generated from this graph.

---

# Why a Knowledge Graph?

A graph-based model naturally represents professional relationships.

Example:

```text
Candidate
   │
WORKED_AT
   │
Company
   │
DELIVERED
   │
Project
   │
RESULTED_IN
   │
Achievement
   │
SUPPORTED_BY
   │
Evidence
```

This mirrors how careers evolve in the real world.

---

# Benefits

## Single Source of Truth

Every career artifact references the same structured information.

Updating an achievement automatically improves every downstream output.

---

## Rich Relationships

Graphs make it easy to answer questions such as:

* Which skills were demonstrated in Project X?
* Which achievements support Leadership?
* Which experiences match a target job description?
* Which projects demonstrate Python expertise?

---

## Better AI Reasoning

AI agents receive structured context instead of isolated documents.

This enables:

* Better resume generation
* Smarter interview questions
* Stronger recommendations
* More consistent outputs

---

## Extensibility

Future entities can be added without redesigning the data model.

Examples:

* Publications
* Awards
* Patents
* Volunteer Experience
* Professional Memberships
* Learning History

---

## Career Memory

The graph naturally supports long-term career tracking.

As users gain promotions, certifications, projects, and new skills, the graph evolves rather than requiring new documents to be created.

---

# Alternatives Considered

## Alternative 1 — Resume as Source of Truth

**Rejected**

Reason:

Resumes are presentation documents, not structured data models.

---

## Alternative 2 — Relational Database Only

**Partially Accepted**

Reason:

Relational databases remain appropriate for operational data such as user accounts, authentication, and application settings.

However, representing career relationships solely through relational tables introduces unnecessary complexity for reasoning tasks.

---

## Alternative 3 — JSON Documents

**Rejected**

Reason:

JSON is suitable for data exchange but does not naturally represent complex, interconnected relationships or support relationship-based queries.

---

# Consequences

## Positive

* Better reasoning capabilities.
* Cleaner separation between data and presentation.
* Easier feature expansion.
* Consistent outputs.
* Strong foundation for multi-agent AI workflows.

## Challenges

* Increased implementation complexity.
* Additional learning curve for contributors unfamiliar with graph concepts.
* Potential need for a graph database in future versions.

These trade-offs are acceptable because they align with the long-term vision of CareerOS.

---

# Implementation Notes

The Knowledge Graph is a logical architectural concept.

The initial MVP may represent the graph using relational models or JSON while the platform evolves.

Future versions may adopt a dedicated graph database such as Neo4j if justified by project requirements.

This decision keeps the architecture flexible while preserving the conceptual model.

---

# Decision Summary

CareerOS adopts a Career Knowledge Graph because careers are networks of related experiences rather than collections of isolated documents.

The graph becomes the foundation for:

* Resume Generation
* LinkedIn Generation
* Interview Preparation
* Career Coaching
* Job Matching
* Recruiter Simulation
* Future AI Agents

This decision establishes the Knowledge Graph as the central data model for the platform.

---

# Status

**Accepted**

This ADR establishes one of the core architectural principles of CareerOS and should only be revisited if the platform's data model undergoes a fundamental redesign.

---

# Related Documents

* COS-ARCH-001 — System Overview
* COS-ARCH-002 — Software Architecture Specification
* COS-ARCH-003 — Technology Stack Specification
* COS-ADR-001 — Why CareerOS Exists

---

# Revision History

| Version | Date       | Description |
| ------- | ---------- | ----------- |
| 0.1.0   | 2026-06-27 | Initial ADR |
