# Candidate Schema Specification

**Project:** CareerOS
**Document ID:** COS-KG-002
**Version:** 0.1.0
**Status:** Draft
**Sprint:** COS-004.2
**Owner:** CareerOS Core Team
**Last Updated:** 2026-06-27

---

# 1. Purpose

The Candidate entity represents the primary user of CareerOS.

It serves as the root entity within the Career Knowledge Graph. Every other entity—such as Experience, Education, Skills, Projects, and Achievements—is connected directly or indirectly to the Candidate.

The Candidate entity does not store presentation artifacts (e.g., resumes or cover letters). Instead, it stores structured career information from which those artifacts can be generated.

---

# 2. Business Purpose

The Candidate entity provides a single, reusable representation of a person's professional identity.

This allows CareerOS to:

* Generate multiple career artifacts from one source.
* Track career growth over time.
* Maintain consistency across all outputs.
* Support long-term career memory.

---

# 3. Entity Overview

| Property       | Value                                                                 |
| -------------- | --------------------------------------------------------------------- |
| Entity Name    | Candidate                                                             |
| Primary Key    | candidate_id                                                          |
| Parent Entity  | None                                                                  |
| Child Entities | Experience, Education, Skills, Projects, Certifications, Achievements |
| Versioned      | Yes                                                                   |

---

# 4. Field Definitions

| Field              | Type     | Required | Description               |
| ------------------ | -------- | -------- | ------------------------- |
| candidate_id       | UUID     | Yes      | Unique identifier         |
| first_name         | String   | Yes      | Candidate's first name    |
| last_name          | String   | Yes      | Candidate's last name     |
| preferred_name     | String   | No       | Preferred display name    |
| email              | String   | Yes      | Primary email             |
| phone              | String   | No       | Contact number            |
| location           | String   | No       | Current city and country  |
| linkedin_url       | URL      | No       | LinkedIn profile          |
| github_url         | URL      | No       | GitHub profile            |
| portfolio_url      | URL      | No       | Portfolio website         |
| current_title      | String   | No       | Current job title         |
| years_experience   | Decimal  | No       | Total years of experience |
| career_summary     | Text     | No       | Professional summary      |
| target_roles       | Array    | No       | Desired job roles         |
| target_industries  | Array    | No       | Preferred industries      |
| work_authorization | String   | No       | Employment eligibility    |
| created_at         | DateTime | Yes      | Record creation timestamp |
| updated_at         | DateTime | Yes      | Last update timestamp     |

---

# 5. Relationships

The Candidate entity has the following relationships.

```text
Candidate

├── HAS_EXPERIENCE

├── HAS_EDUCATION

├── HAS_SKILL

├── HAS_PROJECT

├── HAS_CERTIFICATION

├── HAS_ACHIEVEMENT

├── HAS_LANGUAGE

├── HAS_AWARD

└── TARGETS_JOB
```

The Candidate is the root node of the Career Knowledge Graph.

---

# 6. Validation Rules

The following validation rules apply.

### candidate_id

* Must be unique.
* Must be a valid UUID.

### email

* Must follow valid email format.
* Should be unique.

### years_experience

* Cannot be negative.
* Recommended maximum: 60 years.

### URLs

* Must begin with https://
* Optional.

### created_at

* Automatically generated.

### updated_at

* Automatically updated.

---

# 7. Example JSON

```json
{
  "candidate_id": "7c17fa9c-1cb8-4fb2-a33d-10d81d40c5aa",
  "first_name": "Aditya",
  "last_name": "Pawar",
  "preferred_name": "Aditya",
  "email": "aditya@example.com",
  "location": "Mumbai, India",
  "linkedin_url": "https://linkedin.com/in/aditya",
  "github_url": "https://github.com/aditya",
  "current_title": "Data Analyst",
  "years_experience": 5,
  "career_summary": "Data Analyst with expertise in analytics, internal audit, automation, and AI.",
  "target_roles": [
    "Senior Data Analyst",
    "Machine Learning Engineer"
  ],
  "target_industries": [
    "Technology",
    "Consulting"
  ]
}
```

---

# 8. AI Usage

The Candidate entity is consumed by:

* Interview Engine
* Resume Engine
* Cover Letter Engine
* LinkedIn Engine
* ATS Engine
* Recruiter Simulation
* Career Coach

It acts as the entry point for every AI workflow.

---

# 9. Future Extensions

Future versions may include:

* Salary history
* Promotion history
* Career goals
* Personality preferences
* Learning roadmap
* Certifications in progress
* Work preferences
* Relocation preferences
* Visa status

These additions should preserve backward compatibility.

---

# 10. Related Documents

* Career Knowledge Graph Specification
* Experience Schema
* Education Schema
* Skill Schema
* Achievement Schema

---

# 11. Revision History

| Version | Date       | Description              |
| ------- | ---------- | ------------------------ |
| 0.1.0   | 2026-06-27 | Initial Candidate Schema |
