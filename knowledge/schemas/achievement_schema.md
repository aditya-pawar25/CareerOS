# Achievement Schema Specification

**Project:** CareerOS  
**Document ID:** COS-KG-006  
**Version:** 0.1.0  
**Status:** Draft  
**Sprint:** COS-004.6  
**Owner:** CareerOS Core Team  
**Last Updated:** 2026-06-27

---

# 1. Purpose

The Achievement entity represents a measurable outcome or accomplishment resulting from a candidate's work.

Unlike Responsibilities, which describe duties performed, Achievements describe the value created through those duties.

Achievements are among the most important entities in CareerOS because they directly influence resume quality, interview performance, and recruiter perception.

---

# 2. Business Purpose

Achievements enable CareerOS to:

- Identify measurable business impact.
- Generate strong resume bullet points.
- Build STAR interview stories.
- Match achievements to job descriptions.
- Highlight leadership and ownership.
- Quantify candidate contributions.

---

# 3. Entity Overview

| Property | Value |
|----------|-------|
| Entity Name | Achievement |
| Primary Key | achievement_id |
| Parent Entity | Project |
| Child Entities | Evidence |
| Versioned | Yes |

---

# 4. Field Definitions

| Field | Type | Required | Description |
|--------|------|----------|-------------|
| achievement_id | UUID | Yes | Unique identifier |
| project_id | UUID | Yes | Parent Project |
| title | String | Yes | Short achievement title |
| description | Text | Yes | Detailed achievement description |
| category | Enum | Yes | Cost Saving, Revenue Growth, Automation, Quality, Productivity, Compliance, Customer Impact, Leadership, Innovation |
| impact_type | Enum | Yes | Financial, Operational, Technical, Strategic |
| measurable | Boolean | Yes | Indicates whether impact is quantified |
| metric_name | String | No | Name of measured metric |
| metric_before | String | No | Baseline value |
| metric_after | String | No | Final value |
| improvement_percentage | Decimal | No | Percentage improvement |
| business_impact | Text | Yes | Business outcome |
| confidence_score | Decimal | No | AI confidence (0–1) |
| created_at | DateTime | Yes | Record creation timestamp |
| updated_at | DateTime | Yes | Last update timestamp |

---

# 5. Relationships

Achievements connect projects with measurable outcomes.

```text
Project
      │
HAS_ACHIEVEMENT
      ▼
Achievement
      ├── DEMONSTRATES → Skill
      ├── SUPPORTED_BY → Evidence
      ├── CONTRIBUTES_TO → Business Goal
      └── USED_IN → Resume Bullet
```

Achievements become reusable across multiple outputs.

---

# 6. Validation Rules

### achievement_id

- Must be unique.
- Must be a valid UUID.

### title

- Required.
- Maximum 120 characters.

### description

- Required.
- Minimum recommended length: 50 characters.

### improvement_percentage

- Range: 0–1000.

### confidence_score

- Range: 0.0–1.0.

### measurable

If `true`, at least one measurable metric should be provided.

---

# 7. Example JSON

```json
{
  "achievement_id": "ACH-001",
  "project_id": "PROJ-001",
  "title": "Automated Procure-to-Pay Audit Analytics",
  "description": "Designed Python automation to identify duplicate invoices, delayed payments, and vendor anomalies, significantly reducing manual audit effort.",
  "category": "Automation",
  "impact_type": "Operational",
  "measurable": true,
  "metric_name": "Manual Analysis Time",
  "metric_before": "20 hours",
  "metric_after": "5 hours",
  "improvement_percentage": 75,
  "business_impact": "Reduced audit execution time while improving audit coverage and consistency.",
  "confidence_score": 0.96
}
```

---

# 8. AI Usage

The Achievement entity is consumed by:

- Resume Engine
- STAR Story Generator
- Interview Coach
- ATS Engine
- Recruiter Simulator
- Career Coach
- Performance Summary Generator

AI agents prioritize achievements because they demonstrate value rather than responsibilities.

---

# 9. Future Extensions

Future versions may include:

- Evidence strength score
- Business KPI mapping
- Team contribution percentage
- Awards received
- Customer testimonials
- Supporting documents
- Impact timeline
- Verification status

---

# 10. Related Documents

- Project Schema
- Responsibility Schema *(planned)*
- Skill Schema
- Evidence Schema
- Career Knowledge Graph Specification

---

# 11. Revision History

| Version | Date | Description |
|----------|------|-------------|
| 0.1.0 | 2026-06-27 | Initial Achievement Schema |