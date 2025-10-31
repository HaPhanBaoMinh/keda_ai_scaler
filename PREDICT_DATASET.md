# Microservice Resource Prediction Dataset

## Overview
This dataset simulates real-world **microservice performance metrics** collected from a Kubernetes-based distributed system.  
It is designed for **training and evaluating machine learning models** that predict future CPU usage, detect anomalies, or optimize autoscaling behavior across multiple microservices.

---

## Dataset Purpose
The dataset represents **multi-dimensional operational data** across services, nodes, and pods, aiming to:
- Predict CPU usage in the next time window (e.g., +5 minutes).  
- Identify abnormal resource consumption patterns.  
- Optimize replica scaling decisions dynamically based on workload trends.  
- Support AI-driven cost optimization and predictive scaling in cloud environments.

---

## Data Schema

| Column | Type | Description |
|--------|------|-------------|
| `timestamp` | datetime | Observation timestamp (UTC). |
| `service_name` | string | Identifier of the microservice (e.g., `auth-service`). |
| `req_count` | int | Number of requests processed in the interval. |
| `req_latency_p95` | float | 95th percentile latency in milliseconds. |
| `error_rate` | float | Percentage of failed requests. |
| `cpu_usage` | float | CPU usage (%) at the current timestamp. |
| `memory_usage` | float | Memory consumption (MB). |
| `cpu_request` | float | CPU request configured per pod (millicores). |
| `memory_request` | float | Memory request configured per pod (MB). |
| `cpu_limit` | float | CPU limit configured per pod (millicores). |
| `memory_limit` | float | Memory limit configured per pod (MB). |
| `replica_count` | int | Current replica count of the service. |
| `pod_count` | int | Total number of active pods in the cluster. |
| `node_count` | int | Total number of active nodes. |
| `instance_type` | string | Node instance type (e.g., `t3.medium`, `m5.large`). |
| `hpa_target_cpu` | float | CPU utilization target set in Horizontal Pod Autoscaler. |
| `hpa_min` | int | Minimum number of replicas allowed by HPA. |
| `hpa_max` | int | Maximum number of replicas allowed by HPA. |
| `day_of_week` | int | Day of the week (0=Monday … 6=Sunday). |
| `hour_of_day` | int | Hour of the day (0–23). |
| `deploy_flag` | int | Flag indicating deployment activity (1=recent deploy). |
| `cpu_usage_next_5m` | float | **Label** — predicted CPU usage 5 minutes later. |

---

## Example Records

```csv
timestamp,service_name,req_count,req_latency_p95,error_rate,cpu_usage,memory_usage,cpu_request,memory_request,cpu_limit,memory_limit,replica_count,pod_count,node_count,instance_type,hpa_target_cpu,hpa_min,hpa_max,day_of_week,hour_of_day,deploy_flag,cpu_usage_next_5m
2025-10-31 10:00:00,auth-service,2400,120,0.8,65.2,512,250,512,500,1024,3,48,6,m5.large,75,2,6,4,10,0,67.4
2025-10-31 10:00:00,order-service,3100,180,1.2,72.5,640,300,768,600,1536,4,48,6,m5.large,80,3,8,4,10,0,75.1
2025-10-31 10:00:00,payment-service,950,250,0.3,48.3,384,200,512,400,1024,2,48,6,t3.medium,70,1,4,4,10,0,50.2