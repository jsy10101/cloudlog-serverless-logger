# cloudlog-serverless-logger

A fault‑tolerant, serverless log aggregation pipeline built with **AWS Lambda**, **Amazon SQS**, and **CloudWatch**.  
Designed to ingest, queue, process, and store application logs at scale—while providing robust retry logic, dead‑letter queues, and centralized observability for production‑grade diagnostics.

---

## 🛠 Tech Stack

-   **AWS Lambda (Python 3.9)** – serverless compute for ingestion and processing
-   **Amazon SQS + Dead‑Letter Queue** – reliable, decoupled message buffering with built‑in retries
-   **Amazon S3** – durable, cost‑effective storage for processed logs
-   **Amazon CloudWatch** – metrics, logs, alarms, and dashboards for observability
-   **Infrastructure as Code** – AWS SAM (or Terraform) for reproducible deployments
-   **Local Development** – Serverless Framework or SAM CLI for offline testing
-   **CI/CD** – GitHub Actions for automated build & deployment

---

## 🚀 MVP Roadmap

### v0.1 – Log Ingestor

-   Define an HTTP endpoint to receive raw log payloads
-   Implement **log_ingestor** Lambda to validate and enqueue messages into SQS
-   Configure a primary SQS queue with a Dead‑Letter Queue for failed deliveries
-   Emit a basic ingestion metric (`IngestedLogCount`) to CloudWatch

### v0.2 – Processor & Storage

-   Add **log_processor** Lambda to batch‑read from SQS and persist logs to S3
-   Publish processing metrics (`ProcessedLogCount`, `ProcessingErrors`) to CloudWatch
-   Configure DLQ redrive policy and alarm on queue depth
-   Assemble a CloudWatch dashboard to visualize ingestion vs. processing rates and error trends

---

## 📖 Initial Roadmap (beyond v0.2)

-   **v0.3** – Alerts & CI/CD

    -   Define CloudWatch alarms for SLA breaches and error thresholds
    -   Automate deployments with GitHub Actions

-   **v0.4** – Query Interface

    -   Develop a simple UI or CLI for querying recent log entries or S3 partitions

-   **v0.5** – Advanced Analytics
    -   Integrate with Grafana/OpenSearch for full‑featured log exploration and anomaly detection.
