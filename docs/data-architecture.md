# Data Architecture

## 1. Architecture Overview

The Attendance Intelligence Dashboard uses a server-mediated reporting architecture to retrieve and process workforce attendance information from Google BigQuery.

At a high level, the data flow is:

1. Workforce attendance information is maintained in Google BigQuery.
2. Server-side application functions retrieve the required reporting data.
3. SQL-based transformations and aggregations prepare the information for analysis.
4. The dashboard presents the resulting metrics, charts, filters, and employee-level details.
5. Users explore the information through the Attendance Overview and Employee Insights modules.

## 2. Technology Stack

| Layer | Technology | Purpose |
|---|---|---|
| Dashboard platform | Lovable | Dashboard experience and deployment |
| Application framework | TanStack Start | Application framework and rendering |
| UI framework | React | Interactive user interface |
| Navigation | TanStack Router | Dashboard routing and navigation |
| Data management | TanStack Query | Data fetching and caching |
| Data source | Google BigQuery | Workforce attendance reporting data |
| Styling | Tailwind CSS | Responsive interface styling |
| UI components | Shadcn UI / Radix UI | User interface components |
| Visualizations | Recharts | Analytical charts |
| Date handling | Date-fns | Date calculations and formatting |

Technology details should be kept consistent with the actual deployed application.

## 3. Data Source

Google BigQuery serves as the analytical data source for the dashboard.

The reporting data includes information relating to:

- Employee records
- Attendance events
- Clock-in and clock-out times
- Working hours
- Attendance status
- Leave information
- Punctuality indicators

Additional available workforce data may support future reporting enhancements.

## 4. Data Processing

The reporting layer applies business rules to prepare attendance information for dashboard consumption.

Key processing activities include:

- Attendance status classification
- Date-based filtering
- Department and manager filtering
- Time normalization
- Attendance credit calculations
- Working-hours aggregation
- Employee-level summaries
- Department-level comparisons

## 5. Application and Data Access

Database access is handled through server-side application functions.

Database credentials and connection details should remain outside the browser and must never be committed to the public repository.

The public portfolio documentation intentionally describes the architecture at a high level without exposing private connection settings or infrastructure identifiers.

## 6. Reporting Experience

Processed reporting information is presented through:

- KPI summaries
- Attendance distribution charts
- Department comparisons
- Attendance trend charts
- Employee summary tables
- Monthly attendance calendars
- Daily attendance history

## 7. Security and Privacy Considerations

The public portfolio repository must not contain:

- Database credentials or access tokens
- Private cloud project or dataset identifiers
- Internal table references
- Employee names or codes
- Personal email addresses or phone numbers
- Private profile image URLs
- Confidential organizational records

Screenshots and demonstration materials should be reviewed and sanitized before publication.

## 8. Future Enhancements

Potential extensions include:

- Employee leave-balance reporting
- Workforce performance analytics
- Attendance and performance comparisons
- Downloadable executive reports
- Additional reporting and export options

These are proposed enhancements and should not be represented as currently implemented features.
