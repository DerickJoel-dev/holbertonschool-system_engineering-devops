
# Web Infrastructure Design

This project focuses on understanding and designing web infrastructure using whiteboard diagrams. It covers how web systems are structured, scaled, secured, and monitored.

## 📁 Project Structure

Each task includes a diagram (whiteboard-style) with explanations:

### 0. Simple web stack

- **1 Server** (IP: 8.8.8.8)
- Domain: `www.foobar.com` pointing to the server (A record)
- Components:
  - Nginx (web server)
  - Application server
  - Code base
  - MySQL (database)

**Issues**:
- Single Point of Failure (SPOF)
- Downtime during maintenance
- Cannot handle high traffic

---

### 1. Distributed web infrastructure

- **1 Load Balancer** (HAProxy)
- **2 Servers** (each contains):
  - Nginx
  - Application server
  - Code base
  - MySQL (Primary + Replica)

**Concepts covered**:
- Load balancing (Round Robin / Least Connections)
- Active-Active setup
- Primary-Replica DB (writes to Primary, reads from Replica)

**Issues**:
- SPOF at load balancer (if not clustered)
- No HTTPS, no firewall
- No monitoring

---

### 2. Secured and monitored web infrastructure

- **HTTPS enabled** (SSL certificate)
- **3 Firewalls**
- **Monitoring clients** (e.g., for SumoLogic)

**Concepts covered**:
- Why HTTPS matters (encrypts traffic)
- Firewall purpose (blocks unauthorized access)
- Monitoring (e.g., QPS, logs, metrics)

**Issues**:
- SSL termination at load balancer (not end-to-end)
- Only one MySQL writable node
- All-in-one servers may not scale well

---

### 3. Scale up

- **New server added**
- **Clustered load balancer**
- **Split services**:
  - Web server on one
  - App server on another
  - DB on a dedicated machine

**Goal**: Scalability and better resource separation.

---

# Author

Derick Quinones

