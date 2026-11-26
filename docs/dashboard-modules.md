# Dashboard Modules

## 1. Overview

The Workforce Attendance Intelligence Dashboard consists of two primary modules:

1. Attendance Overview
2. Employee Insights

Together, these modules support both high-level workforce monitoring and detailed employee attendance analysis.

## 2. Attendance Overview

**Route:** `/`

The Attendance Overview provides an organization-level view of workforce attendance.

### KPI Summary

The dashboard presents nine key indicators:

- Active Employees
- Present Employees on the Latest Available Date
- Absent Employees on the Latest Available Date
- Employees on Leave
- Employees on Week Off
- Attendance Rate
- Average Working Hours
- Average Clock-In Time
- Average Clock-Out Time

### Visual Analytics

The overview includes:

- Attendance Status Distribution: A visual breakdown of attendance categories.
- Department Attendance Comparison: A comparison of attendance rates across departments.
- Attendance Trends: A multi-day view of present, absent, and leave patterns.

### Filters and Reporting

Users can explore the dashboard through:

- Date presets
- Custom date ranges
- Department selection
- Reporting-manager selection
- Filtered workforce summary export

### Employee Summary Directory

The employee directory provides a consolidated view of employee attendance information, including department, reporting manager, attendance rate, attendance counts, and average working hours.

Selecting an employee opens the corresponding Employee Insights view.

## 3. Employee Insights

**Route:** `/insights`

The Employee Insights module provides a detailed view of an individual employee's attendance.

### Employee Selection

Users can search and select employees using the available employee selector. The selected reporting period is preserved when switching between employees.

### Employee Profile

The profile area displays available employee information such as designation, department, location, reporting manager, and joining information.

### Daily Attendance Status

The attendance widget displays the employee's attendance status for the current calendar date in Indian Standard Time, based on the available attendance data.

### Individual Attendance KPIs

The module presents:

- Active shifts
- Days present
- Days absent
- Approved leave days
- Half days
- Late arrivals
- Early departures
- Average working hours
- Average clock-in and clock-out times

### Monthly Attendance Calendar

The calendar presents daily attendance categories using visual status indicators:

- Present
- Half Day
- Leave
- Absent
- Week Off or Holiday

Available attendance details can be inspected through calendar interactions.

### Daily Attendance History

The attendance history provides a chronological record of available daily attendance information, including date, status, leave type, clock-in, clock-out, working hours, and punctuality indicators.

The history supports text-based searching.

## 4. Navigation and User Experience

The dashboard supports navigation between organization-level and employee-level reporting.

Date and employee selections are designed to support a consistent exploration experience. The interface also uses a responsive layout for desktop, tablet, and mobile screens.

## 5. Reporting Scope

The current scope focuses on workforce attendance analytics. Leave-balance reporting, employee performance analysis, and additional downloadable report formats are potential future enhancements.
