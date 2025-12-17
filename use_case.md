# Use Case

## Problem Statement
Radiology turnaround time (TAT) is the time from imaging order to receiving the final signed report, and it plays an important role in patient care and overall hospital flow. When turnaround times are delayed, clinical decisions slow down and downstream processes such as emergency department disposition, inpatient treatment planning, and discharges can be affected. A common challenge is that operational teams often do not have a simple, consistent way to upload workflow data and quickly identify where delays occur.

Although radiology departments generate large amounts of workflow data, this information is often stored in raw exports that are difficult to analyze consistently. Operational teams frequently lack a simple, repeatable way to upload workflow data and quickly identify where delays occur across imaging modalities, priorities, or time periods. As a result, performance issues are often identified reactively rather than proactively.

## Solution
A cloud-based analytics pipeline designed to support operational monitoring of radiology turnaround time. The system would allow users to upload radiology workflow data as CSV files, automatically clean and standardize the data, and store it in a managed SQL database. Aggregated turnaround time metrics are then presented through a dashboard, allowing users to review trends, identify bottlenecks, and support data-driven operational improvements.

## Target Users
1. **Radiology Operations Managers**: Radiology operations managers use the dashboard to monitor turnaround time trends, compare performance across imaging modalities, and identify periods of increased backlog or delay.

2. **Hospital Flow Leadership (ED and Inpatient Operations)**:
Hospital operations leaders review summarized turnaround time metrics to understand how radiology performance affects patient movement, clinical decision timelines, and overall care flow.

3. **Quality Improvement and Analytics Staff**: 
Quality and analytics teams use historical turnaround time data to track performance over time, support improvement initiatives, and report operational metrics to leadership.


## Data Sources
The system uses radiology workflow data provided as CSV exports from existing operational systems. These files may be generated manually or through scheduled system exports. Typical data fields include:
- `study_id` or `order_id`
- `modality` (CT, MRI, US, XR)
- `priority` (optional)
- `ordered_time`
- `completed_time`
- `final_report_time`

The dataset does not require direct patient identifiers. If identifiers are present, they are removed or tokenized during processing to reduce privacy risk.

## Basic Workflow
1. A radiology operations user uploads a workflow CSV file through a Flask web application.
2. The raw CSV file is stored in Azure Blob Storage to preserve the original data for auditing and potential reprocessing.
3. A scheduled serverless process validates the uploaded file, checks required fields, and standardizes timestamps and formats.
4. Cleaned records are loaded into Cloud SQL (MySQL).
5. The processing job computes turnaround time metrics, such as average and median TAT and counts above defined thresholds, and stores results in summary tables. 
6. The Flask app queries the summary tables and displays trends and bottlenecks through a simple analytics dashboard.
