# Data Preparation

## Overview

The original IT Support Ticket dataset was preserved as the raw data source. A separate working dataset was created for data cleaning, enrichment, and Tableau analysis.

The purpose of the preparation process is to transform the source dataset into a structure suitable for operational and time-series analysis in Tableau.

## Step 1: Preserve Raw Data

The original CSV file was retained without modification:

`data/raw/IT Support Ticket Data.csv`

A separate Excel workbook was created for transformation:

`IT_Support_Tickets_Enhanced.xlsx`

This ensures that the original source data remains unchanged.

## Step 2: Remove Source Index

The original dataset contained an unnamed index column that did not provide analytical value.

The column was removed before creating the analytical dataset.

## Step 3: Create Ticket ID

A unique identifier was created for every support ticket.

Example:

- INC-000001
- INC-000002
- INC-000003

Excel formula used:

`="INC-"&TEXT(ROW()-1,"000000")`

This field provides a unique identifier that can be used for ticket-level analysis and distinct ticket counts in Tableau.

## Step 4: Create Ticket Timestamp

The source dataset did not contain ticket creation dates or timestamps.

To support time-series and operational dashboard analysis, simulated timestamps were generated across approximately six months of activity.

Excel formula used:

`=DATE(2026,2,14)+RAND()*(DATE(2026,8,15)-DATE(2026,2,14))`

The timestamps were formatted as:

`yyyy-mm-dd hh:mm:ss`

Because the Excel `RAND()` function recalculates dynamically, the generated timestamps were converted from formulas to static values using Paste Special → Values.

This prevents timestamps from changing between workbook sessions.

## Data Enrichment Notice

Fields that do not exist in the original source dataset are clearly treated as simulated or derived data.

The simulated timestamps are intended to support demonstration of time-series and near-real-time dashboard functionality in Tableau. They should not be interpreted as actual historical ticket creation timestamps from the source system.

## Step 5: Create Ticket Category

A primary ticket category was derived from the existing `Tags` field.

Categories include:

- Security
- Network
- Outage
- Performance
- Software/Bug
- Hardware
- Account/Access
- Billing
- General Support

The purpose of this transformation was to convert the multi-value Tags field into a single primary category suitable for grouping and filtering in Tableau.

## Step 6: Create Ticket Status

The original dataset did not contain ticket status information.

A simulated `Status` field was created with three operational states:

- Resolved
- In Progress
- Open

Excel's `RAND()` function was used to generate the status distribution.

After generation, the formulas were converted to static values using Paste Special → Values to prevent the statuses from changing during recalculation.

This field is simulated and does not represent actual ticket status information from the original source dataset.

## Step 7: Assign Support Teams

An `Assigned_Team` field was derived from the ticket category using rule-based routing logic.

Examples:

- Security → Security Operations
- Network / Outage → Network Operations
- Software/Bug / Performance → Application Support
- Hardware → Desktop Support
- Account/Access → Identity & Access
- Billing → Business Systems
- General Support → Service Desk

Unlike the simulated Status field, Assigned_Team is a derived field based on predefined business rules.

This field enables analysis of ticket volume and workload across IT support teams in Tableau.
