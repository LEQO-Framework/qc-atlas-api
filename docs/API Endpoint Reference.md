# QC-Atlas REST API Reference

This document provides the complete reference for all available REST API endpoints exposed by the QC-Atlas backend.

Each section is grouped by controller/entity (e.g., Algorithms, Implementations, Publications) and annotated by method type.

---

## 📘 Legend
- `GET`: Retrieve data
- `POST`: Create new resources
- `PUT`: Update existing resources
- `DELETE`: Remove resources

---

## 📂 Algorithms

### `GET /algorithms`
Retrieve a list of all algorithms.

**Example Response:**
```json
[
  {
    "id": "3f5a1b6e",
    "name": "Quantum Fourier Transform",
    "description": "Performs frequency analysis using quantum logic"
  }
]
```

### `POST /algorithms`
Create a new algorithm.

**Example Request:**
```json
{
  "name": "Grover's Algorithm",
  "description": "Search algorithm with quadratic speedup"
}
```

### `PUT /algorithms/{algorithmId}`
Update a specific algorithm by ID.

**Example Request:**
```json
{
  "name": "Updated Name",
  "description": "Updated description"
}
```

### `DELETE /algorithms/{algorithmId}`
Delete a specific algorithm by ID.

---

## 📂 Implementations

### `GET /implementations`
List all implementations.

### `POST /implementations`
Create a new implementation.

### `PUT /implementations/{implementationId}`
Update an existing implementation.

### `DELETE /implementations/{implementationId}`
Delete a specific implementation.

---

## 📂 Publications

### `GET /publications`
Fetch all publications.

### `POST /publications`
Create a new publication.

### `PUT /publications/{publicationId}`
Update publication details.

### `DELETE /publications/{publicationId}`
Remove a publication.

---

## 📂 Tags

### `GET /tags`
Get all tags.

### `POST /tags`
Create a new tag.

### `PUT /tags/{value}`
Update tag metadata.

### `DELETE /tags/{value}`
Remove a tag by value.

---

_This document provides only a summary per endpoint type. See controller-level JavaDocs for full behavior and edge cases._
