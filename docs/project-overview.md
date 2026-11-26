<div align="center">

<img src="https://img.shields.io/badge/HR%20ANALYTICS%20%7C%20BUSINESS%20INTELLIGENCE-0B1F3A?style=for-the-badge&labelColor=0B1F3A&color=0B1F3A" alt="HR Analytics and Business Intelligence" />

# Workforce Attendance Intelligence Dashboard

### HR Analytics & Business Intelligence

**A BigQuery-backed attendance analytics dashboard that turns daily attendance records into consistent workforce KPIs, department comparisons and employee-level insights.**

<br />

<img src="https://img.shields.io/badge/Google%20BigQuery-0B1F3A?style=for-the-badge&logo=googlebigquery&logoColor=white&labelColor=1D4ED8&color=0B1F3A" alt="Google BigQuery" />
<img src="https://img.shields.io/badge/HR%20Analytics-0B1F3A?style=for-the-badge&labelColor=14B8A6&color=0B1F3A" alt="HR Analytics" />
<img src="https://img.shields.io/badge/KPI%20Design-0B1F3A?style=for-the-badge&labelColor=1D4ED8&color=0B1F3A" alt="KPI Design" />
<img src="https://img.shields.io/badge/Dashboard%20Development-0B1F3A?style=for-the-badge&labelColor=14B8A6&color=0B1F3A" alt="Dashboard Development" />

<br /><br />

<a href="#executive-overview">Overview</a> &nbsp;|&nbsp;
<a href="#business-challenge">Challenge</a> &nbsp;|&nbsp;
<a href="#analytical-solution">Solution</a> &nbsp;|&nbsp;
<a href="#dashboard-modules-and-kpi-insights">Modules &amp; KPIs</a> &nbsp;|&nbsp;
<a href="#attendance-kpi-definitions-and-business-logic">KPI Logic</a> &nbsp;|&nbsp;
<a href="#dashboard-screenshots">Screenshots</a> &nbsp;|&nbsp;
<a href="#my-role-and-contribution">My Role</a> &nbsp;|&nbsp;
<a href="#documentation">Documentation</a>

<br /><br />

<a href="https://hr-attendance-dashboard.lovable.app/">
  <img src="https://img.shields.io/badge/%E2%86%97%20VIEW%20LIVE%20DASHBOARD-14B8A6?style=for-the-badge&labelColor=0B1F3A" alt="View live dashboard" />
</a>
&nbsp;
<a href="https://github.com/Nandini-Boda/Workforce-Attendance-Intelligence-Dashboard">
  <img src="https://img.shields.io/badge/GITHUB%20REPOSITORY-0B1F3A?style=for-the-badge&logo=github&logoColor=white&labelColor=0B1F3A" alt="GitHub repository" />
</a>

<sub>The live dashboard is an interactive demonstration. Its data comes from scheduled synchronization, not real-time streaming.</sub>

</div>

---

## Executive Overview

This project is an **HR analytics and workforce reporting solution**. It consolidates attendance records into one reporting view, defines consistent attendance KPIs, and lets users move from an organization-wide picture to an individual employee's attendance history.

**Information consolidated:** active headcount, daily attendance status (present, absent, leave, week off), attendance rate, working hours, clock-in and clock-out times, and punctuality indicators.

| Who benefits | How |
| :-- | :-- |
| **HR teams** | Consolidated attendance reporting and faster employee-level reviews |
| **Department managers** | Department and reporting-manager comparisons |
| **Workforce operations** | Daily workforce status and working-hour patterns |
| **Management** | A consistent attendance rate and trend view for decision-making |

---

## Business Challenge

Attendance reporting commonly runs into practical problems:

- **Fragmented attendance reporting** across sources and formats
- **Difficulty comparing departments** on a like-for-like basis
- **Limited visibility into absence and leave patterns**
- **Manual employee-level attendance reviews**
- **Difficulty monitoring punctuality**
- **Limited visibility into working-hour patterns**
- **No single, consistent set of workforce KPIs**

---

## Analytical Solution

| Analytical step | What it delivers |
| :-- | :-- |
| **BigQuery-backed reporting** | Google BigQuery is the reporting data source for attendance data |
| **Structured attendance data** | Each record is classified into a defined status category |
| **Consistent KPI logic** | Attendance credits and a single attendance-rate formula applied everywhere |
| **Department and manager analysis** | Comparison across departments and reporting managers |
| **Employee drill-down** | From the summary directory into an individual attendance record |
| **Interactive filters and CSV reporting** | Date, department and manager filters, with CSV export of the filtered summary |

The project documentation describes SQL-based aggregation and transformation of the BigQuery data before it reaches the dashboard. The repository does not include query scripts, so no SQL is shown here.

---

## Dashboard Modules and KPI Insights

### 1. Workforce Attendance Overview

An organization-level view for the selected period.

| KPI | Business question it answers |
| :-- | :-- |
| **Total active employees** | How large is the workforce being measured? |
| **Present** | How many employees were at work on the latest date? |
| **Absent** | How many employees were absent without leave? |
| **On leave** | How many employees were on leave? |
| **Week-off workforce** | How many employees were on a scheduled week off or holiday? |
| **Attendance rate** | What share of expected working days was attended? |
| **Average working hours** | How long are employees working on average? |
| **Average clock-in time** | When do employees typically start? |
| **Average clock-out time** | When do employees typically finish? |

### 2. Department-Level Attendance Analysis

A department comparison of attendance rate lets HR and management see which departments sit above or below the rest and decide where to investigate further. Department and reporting-manager filters narrow the view to a specific team.

### 3. Attendance Status Distribution

Shows how the workforce splits across present, absent, leave and week-off statuses, giving a quick read on whether absence or leave is driving a lower attendance rate.

### 4. Attendance Trend Analysis

Multi-day trends of present, absent and leave counts help spot changes in workforce attendance across the selected period, instead of relying on a single day.

### 5. Employee-Level Attendance Analysis

A drill-down for one selected employee, keeping the chosen reporting period.

| Insight | What it shows |
| :-- | :-- |
| **Attendance rate** | The individual's rate under the same KPI logic |
| **Present, absent and approved leave days** | Attendance pattern across the period |
| **Half days** | Partial-day attendance |
| **Late arrivals and early departures** | Punctuality indicators |
| **Average working hours, clock-in and clock-out** | Working-hour and timing patterns |
| **Monthly attendance calendar** | Colour-coded daily statuses at a glance |
| **Daily attendance history** | Day-by-day records, searchable |

### 6. Workforce Reporting and Export

Date presets, custom date ranges and department and manager filters shape the view, and the filtered workforce summary can be exported to CSV for further analysis or sharing. Selections carry between the overview and the employee view.

---

## Attendance KPI Definitions and Business Logic

**Status classification.** Every record is grouped as Present, Half Day, Leave, Absent, Week Off / Holiday, or Other (anything that does not match a defined category).

| Status | Present credit | Leave credit | Absent credit | In attendance-rate denominator |
| :-- | :-: | :-: | :-: | :-: |
| Present | 1 | 0 | 0 | Yes |
| Half Day | 0.5 | 0.5 | 0 | Yes |
| Leave | 0 | 1 | 0 | Yes |
| Absent | 0 | 0 | 1 | Yes |
| Week Off / Holiday | 0 | 0 | 0 | **No** |

**Attendance rate**

```text
Attendance Rate (%) = Present Credits / (Present Credits + Absent Credits + Leave Credits) x 100
```

**The denominator** is the total of present, absent and leave credits. Week-offs and holidays are excluded, so scheduled non-working days do not lower the rate. A half day adds 0.5 to present credits and 0.5 to leave credits.

**Working hours.** Durations are normalized to minutes and displayed as hours and minutes (for example, 495 minutes appears as 8h 15m). Averages use only records with positive working-hour values.

**Punctuality indicators.** Late arrivals, early departures and clock-in and clock-out times are tracked per employee.

**Date presets.** Presets are anchored to the latest available attendance date in the data, not the calendar date.

> Figures support reporting and review. They are not a substitute for HR policy decisions or payroll calculations.

---

## Dashboard Screenshots

<!--
  SCREENSHOT PRIVACY REVIEW (action required before publishing images)
  The three files in Screenshots/ show employee names, employee codes and profile photos.
  Employee Insights.png also shows a date of birth, phone number and work email.
  The brief for this README also says not to expose employee names, IDs or contact details,
  so the images are NOT embedded yet. Once you have confirmed the data is fully synthetic,
  or masked those fields, remove the comment markers around the block below.

<div align="center">

<img src="Screenshots/Overview.png" alt="Attendance Overview dashboard" width="100%" />

<sub><b>Attendance Overview:</b> workforce KPIs, department attendance comparison and status distribution for management review</sub>

<br /><br />

<img src="Screenshots/Overview%202.png" alt="Employee summary directory" width="100%" />

<sub><b>Employee summary directory:</b> sortable attendance rate, counts and average clock times, with a path into employee drill-down</sub>

<br /><br />

<img src="Screenshots/Employee%20Insights.png" alt="Employee Insights dashboard" width="100%" />

<sub><b>Employee Insights:</b> individual KPIs, monthly attendance calendar and daily history for attendance investigation</sub>

</div>
-->

Screenshots are being reviewed for personal information before publication. To see the dashboard in action, use the live dashboard link at the top of this page.

---

## Business Insights and Decision Support

Stakeholders can use the dashboard to investigate questions such as:

- Which departments have lower attendance rates?
- How does attendance vary across the selected period?
- Are absence patterns increasing?
- Which employees show recurring late arrivals?
- Which employees show frequent early departures?
- How do working-hour patterns differ across teams?
- Which employees may need further attendance review?

These are analytical questions the dashboard helps answer. This README does not report findings from the demonstration data.

---

## My Role and Contribution

This is a **collaborative data analytics and dashboard development project**. My contribution focused on:

- Understanding workforce attendance reporting requirements
- Organizing attendance reporting metrics
- Defining and reviewing attendance KPI logic and status classification
- Working with Google BigQuery as the reporting data source
- Translating attendance data into meaningful HR metrics
- Designing executive-level and employee-level reporting views
- Supporting department and employee drill-down analysis
- Shaping filters and the reporting experience
- Presenting workforce information through an interactive dashboard

It is a portfolio demonstration, not a production enterprise HR platform.

---

## Tools and Analytical Skills

| Area | Skills demonstrated |
| :-- | :-- |
| **Analytics and BI** | KPI design, HR and workforce analytics, attendance reporting, data analysis, data visualization, analytical storytelling |
| **Data source** | Google BigQuery as the reporting data source |
| **Dashboard development** | Interactive dashboard with filters, drill-down and CSV export |
| **Supporting platform** | Lovable (with React, Recharts and TanStack-based tooling underneath) |

---

## Business Value

- **Centralized workforce reporting** in one place
- **Consistent attendance measurement** through shared KPI rules
- **Department-level visibility** for fair comparison
- **Faster attendance reviews** through filters and drill-down
- **Better punctuality monitoring** with late and early indicators
- **Employee-level investigation** of attendance history
- **More informed HR and management discussions**

---

## Documentation

| Document | Description |
| :-- | :-- |
| [Project Overview](docs/project-overview.md) | Purpose, audience and key features |
| [Dashboard Modules](docs/dashboard-modules.md) | Modules, KPIs, filters and navigation |
| [Attendance Metrics](docs/attendance-metrics.md) | Status classification and calculation logic |
| [Data Architecture](docs/data-architecture.md) | How the data and reporting layers fit together |

---

## Data Privacy and Demo Disclaimer

This public repository does not expose confidential employee or organizational information. Cloud project identifiers, dataset and table names, connection and authentication details, and employee personal information are intentionally not published. The live dashboard is an interactive demonstration, and its attendance data is subject to scheduled synchronization, not real-time streaming.

---

<div align="center">

**Workforce Attendance Intelligence Dashboard**

<sub>An HR analytics and business intelligence case study: collaborative dashboard development.</sub>

</div>
