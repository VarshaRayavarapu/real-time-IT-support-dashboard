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
