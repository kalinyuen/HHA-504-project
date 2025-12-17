# HHA 504 – Cloud Integration Mini-Capstone
## Radiology Turnaround Time Analytics 

## Project Overview
This project designs a cloud-based solution for analyzing radiology turnaround time (TAT), which is the time from ordering an imaging scan to receiving the final signed report. Delays in turnaround time can impact patient care, emergency department care flow, and overall hospital operations. The solution focuses on building a scalable and secure cloud architecture that takes in operational workflow data, processes and summarizes the data, and presents analytics through a dashboard.

## Healthcare Problem
Radiology departments generate large amounts of workflow data, but often lack efficient tools to turn this data into useful insights. As a result, delays in imaging interpretation which are caused by factors such as backlogs, staffing constraints, or periods of high demand, are difficult to identify and address in a timely way.

Manually reviewing raw data is time-consuming and inconsistent, making continuous monitoring difficult. Without a structured way to analyze turnaround time trends across modalities and time periods, operational teams struggle to identify bottlenecks, focus improvement efforts, and support efficient patient care and hospital operations.

## High-Level Solution
- Upload radiology workflow CSV files through a web interface
- Store raw files in cloud object storage
- Use serverless compute to validate and process the data
- Store cleaned and summarized data in a managed SQL database
- Display analytics and trends through a dashboard

## Cloud Services Used
- **GCP Cloud Run** – Flask web application
- **Azure Blob Storage** – Raw file storage
- **GCP Cloud Scheduler** – Scheduled processing
- **GCP Cloud Functions** – Data processing and aggregation
- **GCP Cloud SQL (MySQL)** – Cleaned data and summary tables
- **GCP Cloud Logging** – Monitoring and troubleshooting

## Repository Structure
```text
assignment_final/
├── architecture_diagram.png
├── architecture_plan.md
├── README.md
├── reflection.md
└── use_case.md
```
