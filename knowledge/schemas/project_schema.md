# Project Schema Specification

**Project:** CareerOS  
**Document ID:** COS-KG-005  
**Version:** 0.1.0  
**Status:** Draft  
**Sprint:** COS-004.5  
**Owner:** CareerOS Core Team  
**Last Updated:** 2026-06-27

---

# 1. Purpose

The Project entity represents a significant initiative, assignment, engagement, or piece of work completed during an Experience.

Projects provide the primary business context for responsibilities, technologies, achievements, business outcomes, and measurable impact.

Unlike an Experience, which describes employment, a Project describes the actual work performed.

---

# 2. Business Purpose

Projects help CareerOS understand:

- What the candidate actually worked on.
- Business problems solved.
- Technologies used.
- Team collaboration.
- Business outcomes.
- Responsibilities performed.
- Skills demonstrated.

Projects become the foundation for generating resume bullet points and interview stories.

---

# 3. Entity Overview

| Property | Value |
|----------|-------|
| Entity Name | Project |
| Primary Key | project_id |
| Parent Entity | Experience |
| Child Entities | Achievement, Evidence |
| Versioned | Yes |

---

# 4. Field Definitions

| Field | Type | Required | Description |
|--------|------|----------|-------------|
| project_id | UUID | Yes | Unique project identifier |
| experience_id | UUID | Yes | Parent Experience |
| project_name | String | Yes | Project title |
| client_name | String | No | Client or business unit |
| domain | String | No | Industry or functional domain |
| project_type | Enum | Yes | Internal, Client, Product, Research, Audit, Automation |
| business_problem | Text | Yes | Problem being solved |
| project_description | Text | Yes | Project overview |
| candidate_role | String | Yes | Candidate's role |
| start_date | Date | No | Project start |
| end_date | Date | No | Project completion |
| project_status | Enum | Yes | Completed, Ongoing, On Hold |
| team_size | Integer | No | Approximate project team size |
| business_value | Text | No | Business impact |
| created_at | DateTime | Yes | Record creation |
| updated_at | DateTime | Yes | Record update |

---

# 5. Relationships

Projects connect multiple entities within the Career Knowledge Graph.

```text
Experience

↓

DELIVERED

↓

Project

├── PRODUCED → Achievement

├── REQUIRED → Skill

├── SUPPORTED_BY → Evidence

├── USED → Technology

└── CONTRIBUTED_TO → Business Goal
```

Projects provide the operational context for professional accomplishments.

---

# 6. Validation Rules

### project_id

- Must be unique.
- Must be a valid UUID.

### project_name

- Required.
- Cannot be empty.

### business_problem

- Required.
- Minimum recommended length: 30 characters.

### project_status

Allowed values:

- Completed
- Ongoing
- On Hold

### team_size

- Cannot be negative.

### start_date

Cannot occur after end_date.

---

# 7. Example JSON

```json
{
  "project_id": "PROJ-001",
  "experience_id": "EXP-001",
  "project_name": "Procure-to-Pay Audit Automation",
  "client_name": "Rossari Biotech Ltd.",
  "domain": "Internal Audit",
  "project_type": "Automation",
  "business_problem": "Manual audit testing consumed significant analyst effort and increased the risk of inconsistent findings.",
  "project_description": "Developed Python-based analytics to automate Procure-to-Pay audit procedures, identify duplicate invoices, payment delays, and vendor anomalies.",
  "candidate_role": "Data Analyst",
  "project_status": "Completed",
  "team_size": 5,
  "business_value": "Reduced manual analysis effort and improved audit coverage."
}
```

---

# 8. AI Usage

Projects are consumed by:

- Resume Engine
- Achievement Mining Engine
- STAR Story Generator
- Interview Preparation Engine
- Recruiter Simulator
- ATS Engine

Projects provide the context required to generate high-quality resume bullets and behavioral interview answers.

---

# 9. Future Extensions

Future versions may include:

- Budget
- Technologies Used
- Stakeholders
- Risks
- Deliverables
- KPIs
- Timeline Milestones
- GitHub Repository
- Documents Produced
- Screenshots
- Architecture Diagrams

---

# 10. Related Documents

- Candidate Schema
- Experience Schema
- Company Schema
- Achievement Schema
- Skill Schema
- Evidence Schema

---

# 11. Revision History

| Version | Date | Description |
|----------|------|-------------|
| 0.1.0 | 2026-06-27 | Initial Project Schema |