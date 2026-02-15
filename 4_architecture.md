# Edge & Factory Floor Layer
- Industrial sensors / PLCs / SCADA
- Edge gateway agents
- Local TSDB (optional)
- On-prem buffering (intermittent connectivity)
- OPC-UA/MQTT connectors

Responsibilities:
- Collect raw sensor data
- Convert proprietary protocols → usable formats
- Send data securely to the cloud
- Support offline inference if needed (edge container)

# Ingestion & Streaming Layer
- Event Hubs / Kafka clusters
- Batch ingestion jobs (ERP/CMMS)
- File ingestion pipelines (manuals, logs, PDFs)
- Schema registry

Responsibilities:
- Real-time streaming data ingestion
- Standardize payloads
- Transport data to the data lake & feature pipelines
- Enforce schema contracts

# Data Lake & Storage Layer
- ADLS (raw → bronze → silver → gold)
- Blob storage (manuals, images, model artifacts)
- SQL/Postgres for metadata
- Time-series store

Responsibilities:
- Store raw and processed data
- Provide versioned datasets for ML
- Persist documents used for RAG
- Store application persistent state

# Feature Engineering & Orchestration Layer
- Airflow / Dagster orchestrator
- Feature store (training + inference features)
- Data quality checks (Great Expectations)

Responsibilities:
- Batch and streaming feature pipelines
- Unified feature definitions
- Automated validation & data drift detection
- Trigger model training & retraining pipelines

# ML Training & Model Registry Layer
- Azure Machine Learning workspace
- Compute clusters for training
- MLflow (experiment tracking + registry)

Responsibilities:
- Train predictive models (PyTorch, Scikit-learn)
- Tune hyperparameters
- Track metrics, artifacts, parameters
- Register versioned models for deployment

# LLM & RAG Layer
- Document loaders / chunkers
- Embedding models (HF/Azure OpenAI)
- Vector database (Milvus / OpenSearch)
- LangChain / LlamaIndex runtime
- LoRA/QLoRA fine-tuning pipelines
- Evaluation (InspectAI / DeepEval)

Responsibilities:
- Ingest & index manuals, notes, logs
- Retrieve relevant context for technician queries
- Power the troubleshooting assistant
- Fine-tune or adapt models with domain data

# Inference & Serving Layer
- FastAPI microservices:
- - Predictive maintenance scoring API
- - Anomaly detection API
- - LLM troubleshooting assistant API
- - Incident similarity search API
- Container images (Docker)
- GPU partitioning (MIG or similar)

Responsibilities:
- Serve ML predictions in real time
- Provide LLM responses
- Handle traffic from UI or ERP systems
- Provide consistent latency in production

# Deployment & Orchestration Layer (Runtime)
- AKS (Azure Kubernetes Service)
- Node pools (CPU, GPU)
- Autoscalers
- API Gateway / Ingress Controller
- Service Mesh

Responsibilities:
- Host microservices & model servers
- Manage scaling & resiliency
- Secure service-to-service networking
- Expose stable production endpoints

# Observability & Monitoring Layer
- Logging (OpenTelemetry / ELK / Azure Monitor)
- Metrics & dashboards (Grafana / Azure Monitor)
- Alerts
- Model drift detection (EvidentlyAI / custom)
- LLM evaluation feedback loops

Responsibilities:
- Monitor service health
- Track model performance degradation
- Detect input drift, data quality issues
- Capture technician feedback on LLM responses

# Security & Compliance Layer
- Azure AD (OIDC authentication)
- RBAC for APIs & dashboards
- Key Vault for secrets
- Private VNETs & Private Endpoints
- Image scanning + SBOM

Responsibilities:
- Authenticate/authorize users
- Protect secrets and credentials
- Ensure data governance & compliance
- Provide secure, isolated workloads

# Application & UX Layer
- Technician web UI
- Supervisor dashboards
- Mobile app (optional)
- Integration with ERP/CMMS (SAP, Maximo)

Responsibilities:
- Alert technicians about upcoming failures
- Allow natural-language troubleshooting
- Provide historical trends & machine health
- Embed into existing enterprise systems

# CI/CD & DevOps Layer
- GitHub Actions workflows (build/test/deploy)
- Infrastructure-as-Code (Bicep/Terraform)
- Container registry (ACR)
- Environment promotion gates

Responsibilities:
- Build and test all microservices
- Deploy containers to AKS
- Register + promote ML models
- Test data pipelines

[![Architecture overview](./img/architecture.png)