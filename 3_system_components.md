# 📊 Data Sources & Producers
- 📈 Industrial sensors / PLCs / SCADA: vibration, temperature, RPM, power, error codes (time series).
- 📑 Maintenance logs: ERP/CMMS work orders, parts replaced, timestamps.
- 📝 Technician notes: unstructured text, images (photos of faults), attachments.
- 📖 Machine manuals / SOPs: PDFs/HTML, structured & unstructured reference.
- 🚨 Event streams: alarms, state changes, line stops.
- 🗃️ IT/OT metadata: machine type, model, installation date, service history.

# Ingestion & Streaming
- On‑prem ingestion: OPC-UA/MQTT collectors, edge gateway agents.
- Streaming: Kafka/Event Hubs (sensor/event ingestion at scale).
- Batch ingestion: Scheduled pulls from ERP/CMMS databases.
- File ingestion: Blob uploads for PDFs/logs/images.
- Schema management: Confluent schema registry / Azure Schema Registry (for typed events).
- Data contracts: Versioned payload definitions between OT teams and AI systems.

# Data Lake & Storage
- Cold storage: Data lake (e.g., ADLS) for raw, bronze, silver, gold zones.
- Time series store: Optimized TSDB (or parquet/Delta with Z-ordering).
- Relational store: Postgres/SQL for app metadata and user/session state.
- Blob storage: Manuals, images, model artifacts.
- Secrets: Key Vault for credentials, API keys, connection strings.

#  Feature & Metadata Management
- Feature store: Centralized computed features for training & inference parity.
- ML metadata: Experiments, params, metrics, artifacts (e.g., MLflow).
- Data lineage: Track sources → transformations → features → models.

#  ETL/ELT & Orchestration
- Pipelines: Batch ETL (daily/hourly) and streaming transforms.
- Orchestrator: Airflow or Dagster for DAGs, retries, SLAs, backfills.
- Quality checks: Great Expectations / custom checks in DAGs.

# Model Development & Training
- Classical/Deep ML: Scikit‑learn (anomaly, classification), PyTorch (seq models).
- Time-series: Windowing/FFT/ASD features; optional deep TCN/LSTM/Transformer.
- Hyperparameter tuning: Built-in Azure ML sweeps or Optuna.
- Experiment tracking: MLflow runs/metrics/artifacts.
- Model registry: Versioning, stage transitions (staging/production/archive).

# LLM / RAG Components
- Document loaders/parsers: PDF/HTML parsers, safety filters.
- Chunking & embedding: HF embedding models or Azure OpenAI embeddings.
- Vector DB: Milvus or OpenSearch for semantic retrieval.
- RAG orchestration: LangChain / LlamaIndex for retrieval + generation.
- Guardrails: Prompt templates, toolformer constraints, output moderation.
- Fine-tuning/PEFT: LoRA / QLoRA pipelines (optional) with eval harness.

# Inference Services (Online & Batch)
- FastAPI services:
- - Predictive maintenance (scoring) API.
- - Anomaly detection API (stream/batch endpoints).
- - LLM troubleshooting chat API (RAG).
- - Similar-case retrieval/API for incidents.
- Batch inference: Nightly risk scoring for all assets.
- Edge inference: On‑prem container for low‑latency or offline sites.

# Deployment & Runtime
- Containerization: Docker images per service.
- Cluster runtime: AKS for microservices and model servers.
- GPU strategy: Nodes with GPUs; partitioning (e.g., MIG) for LLM/embeddings.
- Serverless (optional): Functions for light ETL/webhooks.
- Scaling: HPA on CPU/GPU/utilization, queue depth.
- Blue/green or canary: Gradual rollout of new model/API versions.

# Observability & Monitoring
- Application: Logs, metrics, traces (OpenTelemetry), dashboards, alerts.
- Data quality: Missingness, drift in inputs, schema violations.
- Model performance: Real‑time and post-hoc evaluation, decay monitoring.
- LLM-specific: Hallucination checks, toxicity filters, retrieval diagnostics.
- SLOs/SLAs: Latency, availability, error budgets; on-call runbooks.

# Model & Data Monitoring (AI-specific)
- Drift detection: Feature distribution drift, PSI/KS tests.
- Performance: Ground truth backfill → precision/recall over time.
- Retraining triggers: Threshold-based or scheduled jobs.
- Feedback loop: Technician thumbs-up/down, step helpfulness, escalation logs.

# Security & Compliance
- AuthN/AuthZ: OIDC (Azure AD), RBAC by role (technician, supervisor, admin).
- Network: Private links, VNET integration, ingress with WAF.
- Secrets: Key Vault; short‑lived credentials, managed identities.
- Data governance: PII scanning, retention, DLP tagging.
- Supply chain: Image signing (cosign), SBOM, vulnerability scanning.
- Auditability: Full trace of inputs, prompts, retrieved docs, outputs.

# APIs & Integration
- API Gateway: Routing, rate limits, auth, versioning.
- Webhooks/Events: Alerting to ticketing/ERP; pub/sub for incidents.
- Connectors: ERP/CMMS (e.g., SAP/Maximo) integration adapters.
- SDK/Clients: Internal Python/TS client libraries for consuming services.

# User Interfaces
- Technician UI: Real-time alerts, chat assistant, stepwise guides, photos.
- Supervisor dashboard: Health KPIs, predicted failures, trends, status.
- ML Ops console: Runs, data quality, drift, retraining status.

(UI could be web app, embedded widget in existing CMMS, or Teams app if applicable.)

# CI/CD & Release Engineering
- Pipelines: GitHub Actions workflows (lint, test, build, scan, push, deploy).
- Infra as Code: Bicep/Terraform for Azure resources & AKS.
- Environment strategy: Dev → Staging → Prod with promotion gates.
- Testing: Unit, integration (ephemeral envs), load tests, chaos tests.
- Data pipelines CI: DAG validation, schema tests, data mocks.

# Cost & Capacity Management
- Autoscaling policies: CPU/GPU/queue depth scaling, scale-to-zero for LLMs off-hours.
- GPU utilization: Batching, quantization, MIG partitioning.
- Budget alerts: Cost dashboards & anomaly alerts.
- Caching: Embedding cache, retrieval cache to reduce token costs.

# Edge & Hybrid Considerations
- Edge gateway: Local buffering, intermittent connectivity handling.
- Local models: Minimal anomaly detection when offline.
- Sync: Reliable forwarder with backpressure, exactly-once semantics if possible.

# Data Science Enablement
- Notebooks/Workspaces: Azure ML compute, shared environments.
- Reusable components: Feature transforms, evaluation harnesses, prompt libs.
- Templates: Cookiecutter-style repos for new services/models.

# Governance & Lifecycle
- Model lifecycle: Propose → Review → Stage → Canary → Prod → Sunset.
- Documentation: Architecture ADRs, runbooks, playbooks.
- Access reviews: Periodic RBAC audits.
- Incident management: On-call, severity levels, retrospectives.

# Optional Components
- Distributed compute: Dask/Polars for fast feature engineering.
- Synthetic data: For edge cases in rare failure classes.
- Evaluation frameworks: InspectAI/DeepEval for LLM task quality.
- Retrieval governance: Doc redaction, row-level security in vector store.