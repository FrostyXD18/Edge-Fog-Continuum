# Edge-Fog-Continuum
Implemented an Edge-Fog-Cloud continuum using Docker &amp; Kubernetes, deploying FastAPI microservices and a custom Python scheduler to optimize task execution based on security, data locality, and latency.
## 📌 Project Overview
This project implements an **Edge-Fog-Cloud continuum** to simulate real-world task scheduling across distributed nodes based on **security, data frequency, and latency constraints**.  
It demonstrates how containerized workloads can be efficiently deployed, orchestrated, and monitored in a heterogeneous environment.

## 🎯 Objectives
- Ensure **security-sensitive tasks** run only on **Edge nodes**.  
- Place **high-frequency data tasks** on **Edge/Fog nodes** for low-latency access.  
- Offload **non-sensitive, low-frequency tasks** to the **Cloud**.  
- Simulate realistic delays:
  - Edge: ~1 ms  
  - Fog: ~5 ms  
  - Cloud: ~100 ms  

## 🏗 System Architecture
- **15 Edge Nodes** (low latency, close to users)  
- **10 Fog Nodes** (intermediate layer)  
- **1 Cloud Data Center** (high latency, high compute/storage)  
- **Task Controller** → FastAPI microservice running on each node  
- **Task Scheduler** → Python-based logic deployed as a Kubernetes CronJob  

## ⚙️ Tools & Technologies
- **Docker** → Containerization of Edge, Fog, and Cloud nodes  
- **Kubernetes** → Orchestration of 26-node cluster  
- **FastAPI** → Microservices for task execution decisions  
- **Python** → Task generation & scheduling logic  
- **Prometheus + Grafana** → Monitoring and visualization  

## 🚀 Implementation
1. **Cluster Setup**  
   - Created a Kubernetes cluster with 26 nodes (15 Edge, 10 Fog, 1 Cloud).  
   - Applied labels for node roles (`type=edge`, `type=fog`, `type=cloud`).  

2. **FastAPI Controllers**  
   - Deployed microservices on all nodes to enforce execution rules.  

3. **Task Scheduler**  
   - Implemented custom logic in Python to decide job placement based on security & data constraints.  
   - Packaged scheduler into a Docker container and deployed as a Kubernetes **CronJob**.  

4. **Monitoring**  
   - Collected logs via `kubectl logs`.  
   - Integrated **Prometheus & Grafana** for real-time monitoring of workloads.  

## ✅ Expected Outcomes
- **Sensitive tasks** → Run only on Edge nodes  
- **High-frequency data tasks** → Execute on Edge/Fog nodes  
- **Low-frequency tasks** → Offloaded to Cloud  
- Demonstrated latency-aware scheduling across Edge, Fog, and Cloud layers  

## 📊 Future Enhancements
- Implement **load balancing** for better distribution.  
- Add **resource-aware scheduling** (CPU/memory constraints).  
- Enable **dynamic scaling** of nodes based on workload.

---

👨‍💻 **Author**: [Pritam Roy Chowdhury]  
📌 **Course/Lab Project**: Cloud Continuum with Docker & Kubernetes
