# Daikibo Industrials — Data Analytics & Forensic Technology Job Simulation

A two-part data analytics case study completed as a self-paced **virtual job simulation on Forage** (likely the Deloitte Australia Data Analytics / Technology Job Simulation — confirm exact program name against your completion certificate). The simulation centers on Daikibo Industrials, a fictional manufacturing client, and covers IoT factory telemetry analysis and a gender pay equity audit.

## Project overview

| | |
|---|---|
| **Client (fictional)** | Daikibo Industrials |
| **Format** | Forage virtual job simulation |
| **Tools used** | Tableau Desktop, Microsoft Excel |
| **Tasks completed** | 2 |

---

## Task 1 — Factory telemetry & machine downtime analysis (Tableau)

**Business question:** Daikibo collects telemetry from 9 machine types across 4 factories — Meiyo (Tokyo), Seiko (Osaka), Berlin, and Shenzhen — every 10 minutes. The client wanted to know:
1. Which factory location had the most machine downtime?
2. Which machine types broke down most often at that location?

**Approach:**
- Imported and flattened a month of nested JSON telemetry data (160,704 records) covering May 2021.
- Built a calculated field, `Unhealthy`, assigning 10 minutes of downtime to every "unhealthy" status reading.
- Created two bar charts: *Down Time per Factory* and *Down Time per Device Type*.
- Combined both into a single dashboard and configured the factory chart as an interactive filter, so selecting a factory dynamically updates the device breakdown.

**Key finding:**
- **Factory Seiko** had the highest total downtime (~480 minutes).
- **100% of that downtime** was driven by a single machine type — the **LaserWelder** — pointing to a clear, targeted maintenance priority rather than a systemic issue across all machine types.

**File:** `Daikibo_Dashboard_Screenshot.png`

---

## Task 2 — Gender pay equality audit (Excel)

**Business question:** Following internal complaints about gender pay inequality, the Forensic Tech team built an algorithm producing an "Equality Score" (-100 to +100, where 0 is ideal) for each job role at each factory. The task was to classify every score into a readable category.

**Classification logic:**

| Score range | Class |
|---|---|
| -10 to +10 | Fair |
| -20 to -11, or +11 to +20 | Unfair |
| Below -20, or above +20 | Highly Discriminative |

Implemented as a live Excel formula (not hardcoded), so it recalculates automatically if scores change:
```
=IF(AND(C2>=-10,C2<=10),"Fair",IF(OR(C2<-20,C2>20),"Highly Discriminative","Unfair"))
```

**Key finding:**
- Out of 37 job-role/factory combinations: **19 Fair**, **11 Unfair**, **7 Highly Discriminative**.
- Pay inequality was concentrated almost entirely in **senior leadership roles** (C-Level, VP, Director, Sr. Manager) — every factory showed the same pattern.
- Technical and operational roles (Engineers, Machine Operators, Operational Support) were overwhelmingly classified as **Fair** across all 4 locations.

**File:** `Task_5_Equality_Table_Updated.xlsx`

---

## Skills demonstrated

Data Analysis · Data Modeling · Data Structures · Data Visualization Tools (Tableau) · Spreadsheet Skills (Excel) · Log Analysis · Python Programming · Software Development · Computer Networking · Web Security · Formal Communication · Planning

## Repository contents

```
├── README.md
├── Daikibo_Dashboard_Screenshot.png   # Task 1 — filtered Tableau dashboard
└── Task_5_Equality_Table_Updated.xlsx # Task 2 — classified pay equality data
```

## Key takeaways

- Practiced end-to-end analytics workflow: raw/nested data → cleaning → calculated fields → interactive dashboard → business insight.
- Applied conditional logic (IF/AND/OR) in Excel to turn a sensitive, numeric audit into a clear, defensible three-tier classification system.
- Strengthened the habit of pairing every finding with a concrete, actionable recommendation (e.g., prioritize LaserWelder maintenance at Seiko; investigate pay practices specifically at the senior leadership level).
