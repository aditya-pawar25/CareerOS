# ADR-001: Why CareerOS Exists

**Project:** CareerOS
**Document ID:** COS-ADR-001
**Status:** Accepted
**Date:** 2026-06-27
**Decision Makers:** CareerOS Core Team

---

# Context

Professionals often struggle to describe their work, achievements, and career progression effectively.

While many tools help users format resumes or optimize keywords for Applicant Tracking Systems (ATS), most of them share common limitations:

* They treat the resume as the primary source of information.
* They generate text without understanding the candidate's career.
* They optimize documents rather than helping users understand and communicate their professional experiences.
* Information is repeatedly recreated across resumes, LinkedIn profiles, cover letters, and interview preparation.

This results in duplicated effort, inconsistent career stories, and documents that may not accurately reflect the candidate's experience.

CareerOS aims to solve these problems by focusing on structured career understanding rather than document generation.

---

# Problem

Current career tools are primarily document-centric.

Typical workflow:

```text
Resume
   ↓
AI
   ↓
Improved Resume
```

This approach has several limitations:

* The resume becomes the source of truth.
* Information must be entered repeatedly.
* Achievements are often overlooked.
* Career history is fragmented across multiple documents.
* AI has little context beyond the uploaded file.

As a result, users spend significant time rewriting the same information for different purposes.

---

# Decision

CareerOS will be designed as an **AI Career Intelligence Platform**, not as a resume builder.

Instead of treating the resume as the starting point, CareerOS will maintain a structured representation of the candidate's career.

The platform will:

1. Collect information through adaptive interviewing.
2. Build a structured career profile.
3. Validate information where appropriate.
4. Store reusable career knowledge.
5. Generate multiple career artifacts from the same source of truth.

Resumes, LinkedIn profiles, cover letters, interview preparation, and future outputs are all generated from this structured profile.

---

# Rationale

This approach provides several advantages.

## Single Source of Truth

Career information is stored once and reused consistently across all outputs.

---

## Better Context

AI engines operate on structured career data instead of isolated documents.

---

## Reusability

Users update their career profile rather than recreating every document from scratch.

---

## Consistency

All generated artifacts are aligned because they reference the same underlying data.

---

## Future Expansion

The architecture naturally supports additional capabilities such as:

* Career coaching
* Interview preparation
* Career analytics
* Learning recommendations
* Salary guidance
* Internal talent management

without redesigning the platform.

---

# Alternatives Considered

## Alternative 1 — Traditional Resume Builder

**Rejected**

Reason:

Focuses only on document creation and provides limited long-term value.

---

## Alternative 2 — Resume Optimizer

**Rejected**

Reason:

Improves existing resumes but does not build reusable career knowledge.

---

## Alternative 3 — LinkedIn Optimization Tool

**Rejected**

Reason:

Optimizes only one career artifact rather than the broader career profile.

---

# Consequences

### Positive

* Modular architecture.
* Consistent outputs.
* Better personalization.
* Easier feature expansion.
* Long-term user value.

### Challenges

* More complex initial implementation.
* Requires structured interviewing.
* Additional effort to maintain a career knowledge model.

These trade-offs are considered acceptable given the long-term vision of the project.

---

# Decision Summary

CareerOS is fundamentally a **Career Intelligence Platform**.

Resume generation is one capability of the platform, not its primary purpose.

This decision influences every architectural choice made throughout the project.

---

# Status

**Accepted**

This decision serves as a foundational architectural principle and should only be revisited if the project's core vision changes significantly.

---

# Related Documents

* COS-ARCH-001 — System Overview
* COS-ARCH-002 — Software Architecture Specification
* COS-ARCH-003 — Technology Stack Specification
* COS-ADR-002 — Why a Career Knowledge Graph

---

# Revision History

| Version | Date       | Description |
| ------- | ---------- | ----------- |
| 0.1.0   | 2026-06-27 | Initial ADR |
