# f5-security-logs-elk-k3s-k8s
This repository contains everything you need to run the ELK stack on a single-node K3s cluster, purpose-built to parse and store F5 BIG-IP security logs 🛡️.

📂 Folder Structure
🧾 manifests/
Kubernetes YAML files to deploy:

🟡 Elasticsearch with persistent volume + ILM enabled
🔵 Logstash as a Deployment with mounted ConfigMap
🟢 Kibana with ClusterIP service

🧩 logstash/pipelines/
Logstash pipeline configuration for:

🔐 Parsing F5 security policy logs
📤 Outputting structured events to Elasticsearch
💾 storage/
Volume mount configuration with proper permissions and resource limits for Elasticsearch data

📈 ilm/
Elasticsearch Index Lifecycle Management (ILM) policies for:
Auto rollover
Retention and cleanup

📘 README.md
You're here! Overview of the setup, goals, and next steps.

🚧 Work in Progress
✅ Currently supported: F5 Security logs

⏳ Coming soon: Parsers for Bot Defense, DoS, and AVR logs