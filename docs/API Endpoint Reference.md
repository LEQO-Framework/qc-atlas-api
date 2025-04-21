# LEQO Use Case – QC Atlas & Winery API Endpoints

This document contains the API endpoints from the `qc-atlas-api` and `winery` services that are relevant for the LEQO use case (2024-bloqcat-usecase).

All endpoints are grouped by service and follow the format used in the `bloqCat` repository.

---

## 🧩 Winery Service

**Base URL:** `http://localhost:8080`

### 🔁 Deploy Topology
- `POST /winery/topology/deploy/json`
- **Description**: Deploys a quantum topology described in JSON (with concrete solution node templates and their connections).
- **Request Body Example:**
```json
{
  "nodeTemplates": [
    { "id": "algo-node-1", "type": "qc:ConcreteSolution", "properties": { "qcId": "uuid-abc123" } },
    { "id": "impl-node-1", "type": "qc:ConcreteSolution", "properties": { "qcId": "uuid-def456" } }
  ],
  "relationshipTemplates": [
    {
      "id": "rel-1",
      "type": "qc:DependsOn",
      "source": "algo-node-1",
      "target": "impl-node-1"
    }
  ]
}
