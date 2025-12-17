# Use Case: Radiology Turnaround Time Analytics Dashboard

## Problem Statement
Radiology turnaround time (TAT) is the time from imaging order to final signed report and plays an important role in patient care and overall hospital flow. When turnaround times are delayed, clinical decisions slow down and downstream processes such as emergency department disposition, inpatient treatment planning, and discharges can be affected. A common challenge is that operational teams often do not have a simple, consistent way to upload workflow data and quickly identify where delays occur.

## Solution
A cloud-based data pipeline that takes in radiology workflow CSV files, cleans and standardizes the data, stores it in a managed SQL database, and provides a dashboard with summary analytics (turnaround time trends, bottlenecks, and delay patterns).

## Target Users
1. Radiology operations manager
   - Monitors turnaround times and backlog patterns
   - Identifies workflow bottlenecks by modality or time of day
2. Hospital flow leadership (ED/inpatient operations)
   - Uses summarized turnaround time information to understand care flow constraints
3. Quality improvement / analytics staff
   - Tracks trends over time and supports improvement initiatives

## Data Sources
CSV export with fields such as:
- `study_id` (or order_id)
- `modality` (CT, MRI, US, XR)
- `priority` (optional)
- `ordered_time`
- `completed_time`
- `final_report_time`

## Basic Workflow
1. User uploads radiology workflow CSV through a Flask web app.
2. Raw CSV is stored in Azure Blob Storage.
3. A scheduled serverless job validates and cleans the file, then loads cleaned rows into Cloud SQL (MySQL).
4. The job computes summary statistics (median/avg turnaround times, percent above threshold, etc.) and stores results in summary tables.
5. The Flask app queries summary tables and displays trends and bottlenecks.
