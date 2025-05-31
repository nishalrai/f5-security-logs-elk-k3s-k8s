# f5-security-logs-elk-k3s-k8s
This repository contains everything you need to run the ELK stack on a single-node K3s cluster, purpose-built to parse and store F5 BIG-IP security logs 🛡️.

<br>

📂 Folder Structure<br>
🧾 manifests/<br>
Kubernetes YAML files to deploy:

- 🟡 Elasticsearch with persistent volume + ILM enabled
- 🔵 Logstash as a Deployment with mounted ConfigMap
- 🟢 Kibana with ClusterIP service

<br>

🧩 logstash/pipelines/<br>
Logstash pipeline configuration for:

- 🔐 Parsing F5 security policy logs
- 📤 Outputting structured events to Elasticsearch
- 💾 storage/
Volume mount configuration with proper permissions and resource limits for Elasticsearch data

<br>

📈 ilm/<br>
Elasticsearch Index Lifecycle Management (ILM) policies for:
Auto rollover
Retention and cleanup

<br>

📘 README.md
You're here! Overview of the setup, goals, and next steps.

<br>

🚧 Work in Progress<br>
✅ Currently supported: F5 Security logs

<br>

⏳ Coming soon: Parsers for Bot Defense, DoS, and AVR logs