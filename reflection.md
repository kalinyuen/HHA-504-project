# Reflection

## Area of Confidence
I feel most confident about the overall workflow design and service selection. Each service has a clear role in that Cloud Run provides a simple Flask interface, Azure Blob stores raw uploads for auditability, Cloud Run Jobs/Functions handle cleaning and summarization, and Cloud SQL (MySQL) supports structured queries for the dashboard.

## Area of Uncertainty
The main area of uncertainty is how cross-cloud authentication between GCP services and Azure Blob Storage would be implemented in a production environment. While the overall security principles are well defined, the specific configuration details depend on an organization’s security policies and tooling.

## Alternative Architecture
I considered using Google Cloud Storage for the raw data layer to keep all services within a single cloud provider and reduce complexity. However, Azure Blob Storage was selected to support a multi-cloud design while keeping raw data storage separate from the processing and analytics layers. This maintains a straightforward workflow while allowing flexibility in cloud service selection.

## Next Steps
With more time, I would add stronger authentication, automated data quality checks, and a clear process for handling and reprocessing invalid files. I would also expand dashboard filters and visualizations, along with data retention policies and more formal audit reporting.
