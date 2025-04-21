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
```
- **Response**: Returns a `.qasm` file containing the aggregated quantum circuit.

---

## 📘 QC Atlas API

**Base URL:** `http://localhost:6626`

These endpoints are commonly called in preparation for topology deployment:

### 📄 Retrieve Concrete Solutions
- `GET /concrete-solutions`
- **Description**: Lists all concrete solutions that can be selected as nodes in the Winery topology.

### 📄 Get Concrete Solution by ID
- `GET /concrete-solutions/{id}`
- **Description**: Retrieves the metadata and file contents of a specific concrete solution.
- **Example**: `GET /concrete-solutions/2e458f50-8c32-11ee-b9d1-0242ac120002`

### 📄 Upload File to Concrete Solution
- `POST /concrete-solutions/{concreteSolutionId}/file`
- **Description**: Uploads and attaches a `.qasm` or other relevant file to a concrete solution.
- **Content-Type**: `multipart/form-data`
- **Example**:
```http
POST /concrete-solutions/{id}/file
Content-Type: multipart/form-data

[file=@circuit.qasm]
```

---

## 🔐 Authentication (if applicable)
> Currently, no authentication required for local setup. Future deployments may use Bearer tokens.

---

_This list focuses only on the endpoints actively used by the LEQO use case through UI interactions or deployment logic. For a full API listing, refer to the QC Atlas API documentation._
