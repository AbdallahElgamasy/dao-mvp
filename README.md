# AI Privacy Pipeline (Data Anonymization System)

## Overview

This project implements a **Data Anonymization Orchestrator (DAO)** designed to process and anonymize sensitive data across multiple real-world use cases.

The system supports different input formats:
- CSV (Endpoint Management)
- JSON (Energy & Multi-Site)
- Plaintext Logs (IoT)

It applies privacy-preserving techniques such as:
- Masking
- Hashing / Pseudonymization
- K-Anonymity
- Differential Privacy
- Generalization
- Aggregation

Each technique is dynamically applied depending on the use case.

---

## System Architecture

<p align="center">
  <img width="1536" height="1024" alt="dao_pipeline" src="https://github.com/user-attachments/assets/626faf7c-f099-4c9b-9521-969c22860859" />
</p>

The DAO pipeline consists of:

- **Raw Data Sources**
- **Ingestion Layer**
- **Discovery Engine**
- **Anonymization Engine**
- **Safe Data Transform**
- **Safe Output & Audit**
- **Terminal UI**

---

## Core Components

### Discovery Engine

* Regex detection (implemented)
* NLP (spaCy) – optional
* Presidio – optional

### Anonymization Engine

* Masking
* Hashing
* K-Anonymity
* Differential Privacy

### Safe Data Transform

* Cleaning
* Aggregation
* Feature transformation

### Output Layer

* Anonymized datasets (CSV / TXT)
* Audit logs (JSON)

---

## How to Run

### 1. Create virtual environment

```bash
python -m venv venv
```

### 2. Activate environment

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the pipeline

```bash
python app.py
```

---

## System Behavior

* Automatically loops through all use cases
* Displays formatted results in terminal
* Generates anonymized outputs and audit logs
* Waits 10 seconds between each use case
* Ends with a completion message

---

## Output

Each use case produces:

* Anonymized dataset
* `audit_receipt.json`

### Example:

```json
{
  "pipeline": "DAO-MVP",
  "records_processed": 100,
  "transformations": [
    "masking",
    "generalization",
    "noise injection"
  ],
  "output_file": "..."
}
```

---

## Privacy Design

This system demonstrates that:

* Privacy techniques depend on the data type
* Not all datasets require NLP or advanced PII detection
* Generalization + aggregation can be sufficient for safe analytics
* Differential privacy is used for highly sensitive numeric data

---

## Future Improvements

* Full NLP integration (spaCy / Presidio)
* Real-time streaming (Kafka / MQTT)
* Web dashboard
* Cloud storage integration

---

## Author

**Abdallah Elgamasy**
Software Engineering Student
