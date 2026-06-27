# Career Knowledge Graph Specification

**Project:** CareerOS
**Document ID:** COS-KG-001
**Version:** 0.1.0
**Status:** Draft
**Sprint:** COS-004.1
**Owner:** CareerOS Core Team
**Last Updated:** 2026-06-27

---

# 1. Purpose

This document defines the Career Knowledge Graph (CKG), the central data model of CareerOS.

The Career Knowledge Graph serves as the single source of truth for all candidate information.

Every major feature of CareerOS—including resume generation, LinkedIn optimization, interview preparation, ATS evaluation, recruiter simulation, and future AI agents—operates on this graph rather than directly on documents.

---

# 2. Vision

CareerOS does not store resumes.

CareerOS stores careers.

A resume is simply one presentation of the underlying career knowledge.

The Career Knowledge Graph captures the relationships between a candidate's experiences, projects, achievements, skills, education, certifications, goals, and supporting evidence.

---

# 3. Why a Knowledge Graph?

Professional careers are naturally connected.

For example:

* A project belongs to an experience.
* An achievement results from a project.
* A skill is demonstrated through achievements.
* Evidence supports achievements.
* A job description matches specific skills and experiences.

Representing these relationships explicitly enables more intelligent reasoning than isolated documents.

---

# 4. Design Goals

The Career Knowledge Graph is designed to:

* Maintain a single source of truth.
* Eliminate duplicated information.
* Support AI reasoning.
* Enable reusable career data.
* Improve consistency across outputs.
* Scale as a user's career evolves.

---

# 5. Core Principles

The graph follows these principles:

* Every entity has a unique identity.
* Relationships are first-class citizens.
* Data is reusable.
* Evidence supports important claims.
* Presentation is separated from storage.
* The graph evolves over time.

---

# 6. Core Entities

The initial version of the Career Knowledge Graph contains the following entities:

| Entity           | Purpose                                  |
| ---------------- | ---------------------------------------- |
| Candidate        | Represents the individual using CareerOS |
| Experience       | Employment history                       |
| Company          | Organizations where experience occurred  |
| Project          | Significant initiatives or work          |
| Achievement      | Measurable outcomes                      |
| Skill            | Technical and professional capabilities  |
| Education        | Academic qualifications                  |
| Certification    | Professional certifications              |
| Evidence         | Supporting information for achievements  |
| Job Description  | Target role information                  |
| Resume           | Generated output                         |
| LinkedIn Profile | Generated output                         |

Additional entities may be introduced in future versions.

---

# 7. High-Level Relationships

The Career Knowledge Graph represents relationships rather than isolated records.

Example relationships include:

Candidate

→ HAS_EXPERIENCE → Experience

Experience

→ WORKED_AT → Company

Experience

→ DELIVERED → Project

Project

→ RESULTED_IN → Achievement

Achievement

→ DEMONSTRATES → Skill

Achievement

→ SUPPORTED_BY → Evidence

Candidate

→ HAS_EDUCATION → Education

Candidate

→ HAS_CERTIFICATION → Certification

Candidate

→ TARGETS → Job Description

Resume

→ GENERATED_FROM → Candidate

LinkedIn Profile

→ GENERATED_FROM → Candidate

---

# 8. Graph Characteristics

The graph is:

* Structured
* Extensible
* Versioned
* Explainable
* Machine-readable
* Human-readable

These characteristics allow both AI agents and developers to work from the same representation.

---

# 9. Data Lifecycle

Career information flows through several stages:

1. Information Collection
2. Validation
3. Structuring
4. Relationship Creation
5. Storage
6. AI Consumption
7. Output Generation
8. Continuous Updates

The graph is continuously refined as the user's career evolves.

---

# 10. Consumers of the Graph

The Career Knowledge Graph is consumed by multiple components:

* Interview Engine
* Achievement Mining Engine
* Resume Engine
* LinkedIn Engine
* ATS Evaluation Engine
* Recruiter Simulation Engine
* Career Coach
* Future AI Agents

Each component reads from the graph rather than maintaining its own copy of career data.

---

# 11. Future Expansion

Future versions of the graph may include:

* Publications
* Awards
* Volunteer Experience
* Open Source Contributions
* Patents
* Languages
* Professional Memberships
* Learning History
* Career Goals
* Networking Activities

The graph is intentionally designed for long-term growth.

---

# 12. Related Documents

The following specifications build upon this document:

* Candidate Schema
* Experience Schema
* Project Schema
* Achievement Schema
* Skill Schema
* Evidence Schema
* Relationship Specification
* Validation Rules

---

# 13. Revision History

| Version | Date       | Description                                  |
| ------- | ---------- | -------------------------------------------- |
| 0.1.0   | 2026-06-27 | Initial Career Knowledge Graph specification |
