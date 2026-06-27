# Company Schema Specification

**Project:** CareerOS
**Document ID:** COS-KG-004
**Version:** 0.1.0
**Status:** Draft
**Sprint:** COS-004.4
**Owner:** CareerOS Core Team
**Last Updated:** 2026-06-27

---

# 1. Purpose

The Company entity represents an organization where a candidate has worked or is currently employed.

A Company provides the organizational context for professional experiences, projects, achievements, and responsibilities.

Rather than storing company information repeatedly within each Experience, CareerOS models Company as a separate reusable entity.

---

# 2. Business Purpose

The Company entity enables CareerOS to:

* Avoid duplicate company information.
* Connect multiple experiences to the same employer.
* Provide organizational context.
* Support company-level analytics.
* Improve consistency across resumes and LinkedIn profiles.

---

# 3. Entity Overview

| Property       | Value               |
| -------------- | ------------------- |
| Entity Name    | Company             |
| Primary Key    | company_id          |
| Parent Entity  | None                |
| Child Entities | Experience, Project |
| Versioned      | Yes                 |

---

# 4. Field Definitions

| Field               | Type     | Required | Description                               |
| ------------------- | -------- | -------- | ----------------------------------------- |
| company_id          | UUID     | Yes      | Unique identifier                         |
| company_name        | String   | Yes      | Official company name                     |
| legal_name          | String   | No       | Registered legal entity name              |
| industry            | String   | No       | Primary industry                          |
| company_size        | Enum     | No       | Startup, Small, Medium, Large, Enterprise |
| headquarters        | String   | No       | Headquarters location                     |
| website             | URL      | No       | Official website                          |
| linkedin_url        | URL      | No       | Company LinkedIn page                     |
| description         | Text     | No       | Short company description                 |
| is_current_employer | Boolean  | No       | Indicates if this is the current employer |
| created_at          | DateTime | Yes      | Record creation timestamp                 |
| updated_at          | DateTime | Yes      | Last update timestamp                     |

---

# 5. Relationships

The Company entity connects employment information across the Career Knowledge Graph.

```text
Company

├── EMPLOYS → Experience

├── HAS_PROJECT → Project

├── HAS_INDUSTRY → Industry

└── ASSOCIATED_WITH → Candidate
```

A single Company may be referenced by many candidates and many experiences.

---

# 6. Validation Rules

### company_id

* Must be unique.
* Must be a valid UUID.

### company_name

* Required.
* Cannot be empty.

### website

* Optional.
* Must use HTTPS.

### company_size

Allowed values:

* Startup
* Small
* Medium
* Large
* Enterprise

---

# 7. Example JSON

```json
{
  "company_id": "COM-001",
  "company_name": "Aneja Associates",
  "industry": "Consulting",
  "company_size": "Medium",
  "headquarters": "Mumbai, India",
  "website": "https://www.example.com",
  "description": "Internal Audit and Risk Advisory Firm"
}
```

---

# 8. AI Usage

The Company entity is used by:

* Resume Engine
* LinkedIn Generator
* Interview Engine
* Career Timeline Generator
* Recruiter Simulation
* Job Matching Engine

Company information provides organizational context that helps AI generate more accurate and consistent outputs.

---

# 9. Future Extensions

Future versions may include:

* Company logo
* Revenue range
* Public/private status
* Stock ticker
* Business domains
* Office locations
* Technologies commonly used
* Company culture profile

---

# 10. Related Documents

* Candidate Schema
* Experience Schema
* Project Schema
* Career Knowledge Graph Specification

---

# 11. Revision History

| Version | Date       | Description            |
| ------- | ---------- | ---------------------- |
| 0.1.0   | 2026-06-27 | Initial Company Schema |
