# 🚨 FraudNet: A Graph-Based Fraud Detection System

FraudNet is a real-time fraud detection system that uses **Neo4j** to uncover hidden relationships and suspicious behavior across users, devices, transactions, and more. Designed for production-grade deployment, it detects fraud patterns using graph theory, anomaly detection, and machine learning.

---

## if youre interseting in the stack 
- fraud detection engine + cypher queries in rust
    - neo4rs (rust neo4j driver)
- frontend/ml 
    - rust as brain, python for glue, react for frontend
-  slowly replace other parts with rust as i get more comfortable

## 🧠 System Architecture

### 1. Data Ingestion Layer
- Collects data from:
  - Transaction logs
  - Login events
  - Device fingerprints
  - Geolocation/IP metadata
- Tools: Kafka / PubSub → ETL using Airflow or custom worker scripts

### 2. Graph Database (Neo4j)
- Graph Model:
<br />
    (:User)-[:MADE]->(:Transaction)
<br />
    (:Transaction)-[:TO]->(:Merchant)
<br />
    (:User)-[:USES]->(:Device)
<br />
    (:User)-[:LOCATED_IN]->(:Geo)
<br />
- Uses indexes and constraints for performance

### 3. Analytics & Scoring Engine
- Neo4j Graph Data Science (GDS):
- Community detection (e.g., Louvain)
- Anomaly detection
- Similarity metrics (shared IPs, devices, etc.)
- Optional: ML-based fraud prediction using extracted graph features

### 4. API Layer
- Built with **FastAPI** or **Express.js**
- Key Endpoints:
- `POST /score-transaction`
- `GET /get-user-graph`
- `POST /flag-user`
- `GET /alerts`
- Secured with JWT or OAuth2

### 5. Frontend (Investigation Dashboard)
- **React.js + D3.js or Cytoscape.js**
- Visualizes fraud networks
- Allows fraud analysts to:
- Explore graphs
- Flag or freeze suspicious entities
- Annotate fraud cases

### 6. Alerting System
- Real-time fraud alerts
- Integration options: Email, Slack, Webhooks

### 7. Additional Storage
- PostgreSQL or MongoDB:
- For logs
- Audit trails
- User/session metadata

---

## 🔮 Feature Roadmap

### Phase 1: Core System
- Load data (CSV or real-time API)
- Build graph schema
- Implement basic scoring engine (rule-based + graph metrics)
- Launch admin dashboard

### Phase 2: Intelligence & Detection
- Integrate GDS anomaly scoring
- Train ML models for behavior-based scoring
- Add alert triggers & notifications

### Phase 3: Scalability
- Add Kafka for real-time scoring pipeline
- Support for historical traceability and versioning
- Enable webhook-based fraud responses

### Phase 4: SaaS Mode
- Multi-tenant customer support
- Usage tracking per organization
- Tiered subscription plans

---

## ⚙️ Dev Notes

- Use **APOC** for advanced graph operations
- Modularize Cypher queries and cache responses when needed
- Optional: Implement custom fraud detection logic using PyG or NetworkX

---

## 💡 Example Use Cases
- Detect coordinated fraud rings
- Flag synthetic identities
- Identify compromised devices reused across accounts
- Provide risk scores for transactions in real time

---

## 📈 Tech Stack

| Component         | Tech Used             |
|------------------|-----------------------|
| Graph Database    | Neo4j                 |
| Backend API       | FastAPI / Express.js  |
| ML / Analytics    | scikit-learn / GDS    |
| Frontend          | React.js + D3.js      |
| Stream Processing | Kafka / PubSub        |
| ETL / Scheduling  | Airflow               |
| Data Storage      | PostgreSQL / MongoDB  |

---

## 📬 Contact
Interested in contributing or using this in your org? Reach out or open an issue!
