# Attendance Metrics and Business Logic

## 1. Purpose

This document explains the attendance classifications, calculation principles, and workforce metrics used by the Attendance Intelligence Dashboard.

## 2. Attendance Categories

Attendance records are grouped into the following reporting categories:

| Category | Reporting Treatment |
|---|---|
| Present | Full present credit |
| Half Day | 0.5 present credit and 0.5 leave credit |
| Leave | Full leave credit |
| Absent | Full absent credit |
| Week Off / Holiday | Excluded from the attendance-rate denominator |
| Other | Records that do not match the defined categories |

The classification logic uses the attendance status information available in the source data.

## 3. Attendance Rate

The attendance rate is calculated using present, absent, and leave credits.

\[
\text{Attendance Rate} =
\frac{\text{Present Credits}}
{\text{Present Credits}+\text{Absent Credits}+\text{Leave Credits}}
\times 100
\]

A half-day contributes 0.5 to present credits and 0.5 to leave credits.

Week-offs and holidays are excluded from the denominator so that scheduled non-working days do not reduce the attendance rate.

## 4. Working-Hours Calculation

Time values are normalized into minutes to support consistent calculations.

\[
\text{Total Minutes} =
(\text{Hours}\times60)+\text{Minutes}
\]

Average working hours are calculated using records with positive working-hour values.

Results are converted into readable formats such as:

- 495 minutes → 8h 15m
- 480 minutes → 8h 00m

## 5. Punctuality Indicators

The dashboard includes available indicators for:

- Late arrivals
- Early departures
- Clock-in time
- Clock-out time

These indicators support the review of attendance regularity and working patterns.

## 6. Date-Based Reporting

The dashboard supports predefined reporting periods and custom date ranges.

Date presets use the latest available attendance date as their reporting anchor. This allows the dashboard to work with attendance datasets that may be updated through scheduled synchronization rather than continuous streaming.

## 7. Key Reporting Metrics

| Metric | Business Purpose |
|---|---|
| Active Employees | Understand the active workforce included in reporting |
| Present / Absent | Monitor attendance status |
| Employees on Leave | Review leave-related attendance |
| Week Off | Identify scheduled non-working days |
| Attendance Rate | Evaluate attendance against eligible attendance credits |
| Average Working Hours | Review average recorded work duration |
| Average Clock-In / Clock-Out | Understand workforce punch-time patterns |
| Late Arrivals / Early Departures | Monitor punctuality indicators |

## 8. Calculation Notes

Metrics are subject to the source data, selected date range, employee population, and applied filters.

The dashboard's displayed figures should be interpreted within the defined attendance classification rules. They should not be treated as a substitute for formal HR policy or payroll calculations.
