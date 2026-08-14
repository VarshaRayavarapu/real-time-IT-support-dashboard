# Data Profiling

## Dataset Overview

The source dataset contains IT support ticket records that will be used to develop a Real-Time IT Support & Incident Management Dashboard in Tableau.

### Dataset Size

- Total Records: 29,651
- Total Columns: 5

### Source Columns

| Column | Description |
|---|---|
| Unnamed: 0 | Original row/index identifier |
| Body | Description of the support request |
| Department | Department responsible for the ticket |
| Priority | Priority assigned to the ticket |
| Tags | Categories associated with the ticket |

## Data Quality Assessment

Initial profiling identified:

- No duplicate records
- No missing values in Department
- No missing values in Priority
- No missing values in Tags
- One missing value in Body

Overall, the source dataset has relatively good data quality.

## Priority Levels

The dataset contains three priority levels:

- High
- Medium
- Low

These priority levels will be used to analyze ticket severity and operational workload.

## Departments

The dataset contains tickets across 10 departments, including:

- Technical Support
- Product Support
- Customer Service
- IT Support
- Billing and Payments
- Returns and Exchanges
- Service Outages and Maintenance
- Sales and Pre-Sales
- Human Resources
- General Inquiry

## Tags

Tickets contain tags representing different support topics and technical issues.

Examples include:

- Security
- Network
- Performance
- Bug
- Crash
- Virus
- Outage
- Account
- IT
- Tech Support

These tags may be used to derive ticket categories for dashboard analysis.

## Identified Data Gaps

The original dataset does not contain several fields required for operational and time-series analysis, including:

- Created Timestamp
- Ticket Status
- Resolution Timestamp
- Resolution Time
- SLA Status
- Assigned Support Team
- Location

Therefore, the original dataset will be preserved as the raw data source while an enriched analytical dataset will be created for the Tableau dashboard.
