# Experience Schema Specification

**Project:** CareerOS
**Document ID:** COS-KG-003
**Version:** 0.1.0
**Status:** Draft
**Sprint:** COS-004.3
**Owner:** CareerOS Core Team
**Last Updated:** 2026-06-27

---

# 1. Purpose

The Experience entity represents a professional engagement in a candidate's career.

An Experience typically corresponds to employment at a company but may also represent internships, freelance engagements, consulting assignments, research positions, apprenticeships, or entrepreneurial ventures.

The Experience entity acts as the parent for Projects, Achievements, Responsibilities, and Technologies used during that engagement.

---

# 2. Business Purpose

Experience provides the timeline of a candidate's professional journey.

It enables CareerOS to:

* Build chronological work history.
* Group projects under employers.
* Associate achievements with specific roles.
* Track career progression.
* Measure years of experience.
* Generate resumes and LinkedIn profiles.

---

# 3. Entity Overview

| Property       | Value                |
| -------------- | -------------------- |
| Entity Name    | Experience           |
| Primary Key    | experience_id        |
| Parent Entity  | Candidate            |
| Child Entities | Project, Achievement |
| Versioned      | Yes                  |

---

# 4. Field Definitions

| Field              | Type     | Required | Description                                                          |
| ------------------ | -------- | -------- | -------------------------------------------------------------------- |
| experience_id      | UUID     | Yes      | Unique identifier                                                    |
| candidate_id       | UUID     | Yes      | Owner of the experience                                              |
| company_id         | UUID     | Yes      | Reference to Company entity                                          |
| job_title          | String   | Yes      | Official designation                                                 |
| employment_type    | Enum     | Yes      | Full-time, Part-time, Internship, Contract, Freelance, Self-employed |
| department         | String   | No       | Functional department                                                |
| reporting_manager  | String   | No       | Manager's designation or role                                        |
| start_date         | Date     | Yes      | Employment start date                                                |
| end_date           | Date     | No       | Employment end date                                                  |
| currently_working  | Boolean  | Yes      | Indicates active employment                                          |
| location           | String   | No       | City, State, Country                                                 |
| work_mode          | Enum     | No       | Onsite, Hybrid, Remote                                               |
| employment_summary | Text     | No       | Overview of responsibilities                                         |
| team_size          | Integer  | No       | Approximate team size                                                |
| created_at         | DateTime | Yes      | Record creation timestamp                                            |
| updated_at         | DateTime | Yes      | Last update timestamp                                                |

---

# 5. Relationships

The Experience entity connects multiple parts of the Career Knowledge Graph.

```text
Candidate

↓

HAS_EXPERIENCE

↓

Experience

├── WORKED_AT → Company

├── DELIVERED → Project

├── RESULTED_IN → Achievement

├── USED → Skill

├── SUPPORTED_BY → Evidence

└── TARGETS → Job Description
```

Experience serves as the primary context for most professional accomplishments.

---

# 6. Validation Rules

### experience_id

* Must be unique.
* Must be a valid UUID.

### start_date

* Required.
* Cannot be in the future.

### end_date

* Optional.
* Required if currently_working = false.
* Must be greater than or equal to start_date.

### currently_working

* Boolean only.
* If true, end_date must be null.

### employment_type

Allowed values:

* Full-time
* Part-time
* Internship
* Contract
* Freelance
* Self-employed

### team_size

* Cannot be negative.
* Optional.

---

# 7. Example JSON

```json
{
  "experience_id": "EXP-001",
  "candidate_id": "CAN-001",
  "company_id": "COM-001",
  "job_title": "Data Analyst",
  "employment_type": "Full-time",
  "department": "Internal Audit",
  "start_date": "2023-05-01",
  "end_date": null,
  "currently_working": true,
  "location": "Mumbai, India",
  "work_mode": "Hybrid",
  "employment_summary": "Performed audit analytics, automated reporting, and supported financial audits using Python, SQL, and Power BI.",
  "team_size": 12
}
```

---

# 8. AI Usage

The Experience entity is consumed by:

* Interview Engine
* Achievement Mining Engine
* Resume Engine
* LinkedIn Engine
* ATS Engine
* Career Timeline Generator
* Recruiter Simulation Engine

Experience provides the context needed to understand projects, achievements, and career progression.

---

# 9. Future Extensions

Future versions may include:

* Salary band
* Promotion history
* Performance ratings
* Business unit
* Manager feedback
* Key stakeholders
* Technologies used
* Leadership responsibilities
* KPIs owned

These enhancements should remain backward compatible.

---

# 10. Related Documents

* Candidate Schema
* Company Schema
* Project Schema
* Achievement Schema
* Skill Schema
* Career Knowledge Graph Specification

---

# 11. Revision History

| Version | Date       | Description               |
| ------- | ---------- | ------------------------- |
| 0.1.0   | 2026-06-27 | Initial Experience Schema |
