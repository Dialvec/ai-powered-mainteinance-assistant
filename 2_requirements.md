# Functional requirements
1. Predictive Maintenance
- Detect anomalies from sensor time series
- Predict breakdown probabilities
- Trigger alerts (e.g., vibration increasing abnormally)

2. Troubleshooting Assistant
- Technician asks questions like: “The motor is vibrating and overheats — what should I check first?”
- LLM generates steps using:
- - manuals
- - past incidents
- - technician notes
- - vector database for semantic search

3. APIs for Integration
FastAPI endpoints for:
- Predictions
- Anomaly scores
- Troubleshooting chat
- logs retrieval

4. Deployment Requirements
- Hybrid infrastructure: Azure + on‑prem
- GPU partitioning for LLM inference
- Scalable microservices running on AKS

5. Monitoring
- Model drift detection
- Data quality monitoring
- Logging, tracing, and metrics via standard observability stack

#  Non‑Functional Requirements
- High availability (24/7 operations)
- Low-latency inference (technicians work in real time)
- Security (factories → sensitive IP)
- Cost optimization (LLM inference is expensive)
- Traceability (audit predictions and troubleshooting steps)

#  Success Metrics
- Business KPIs:
- - ↓ Reduce downtime by X%
- - ↓ Reduce unplanned maintenance incidents
- - ↑ Increase technician resolution speed
- - ↑ Better knowledge-sharing across teams

- Technical KPIs
- - Model accuracy / anomaly detection precision
- - API latency under defined thresholds
- - Drift detection false-positive rate
- - Cost per inference reduced through GPU sharing or quantization