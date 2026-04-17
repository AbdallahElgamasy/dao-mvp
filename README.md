# DAO Privacy Pipeline (Data Anonymization Orchestrator)

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
  <img src="dao_pipeline.png" width="900"/>
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

## Project Structure

```text
DAO-MVP/
│
├── app.py
├── iot_edge_security.py
├── README.md
├── requirements.txt
├── dao_pipeline.png
│
├── config/
│   ├── terminal_ui.py
│   ├── usecase_processors.py
│   ├── usecase_runner.py
│   └── usecases.py
│
├── core/
│   ├── differential_privacy.py
│   ├── k_anonymity.py
│   ├── pii_detection.py
│   ├── presidio_masking.py
│   └── transformers.py
│
├── sample_data/
│   ├── csv_input/
│   ├── json_input/
│
├── output/
│   ├── Belgian Use Case Renewable Energy Forecasting/
│   ├── Portuguese Use Case Residential IoT Security/
│   ├── Turkish Use Case Enterprise Endpoint Management/
│   └── UK Use Case Commercial Multi-Site Management/
│
└── venv/
````

---

## Use Cases

### 🇵🇹 Portuguese Use Case – IoT Security

* Regex-based log parsing
* MAC address pseudonymization
* IP masking
* RF generalization

---

### 🇹🇷 Turkish Use Case – Endpoint Management

* K-Anonymity grouping
* Attribute generalization
* Data masking

---

### 🇬🇧 UK Use Case – Multi-Site Management

* Site generalization
* Timestamp rounding
* Session masking

---

### 🇧🇪 Belgian Use Case – Energy Forecasting

* Differential Privacy (noise injection)
* Aggregation & smoothing
* Location precision reduction

---

## Technology Mapping

| Technique            | Portuguese | Turkish | UK | Belgian |
| -------------------- | ---------- | ------- | -- | ------- |
| Regex                | ✔️         | ❌     | ❌ | ❌     |
| Hashing              | ✔️         | ❌     | ❌ | ❌     |
| Masking              | ✔️         | ✔️     | ✔️ | ❌     |
| K-Anonymity          | ❌         | ✔️     | ❌ | ❌     |
| Differential Privacy | ❌         | ❌     | ❌ | ✔️     |
| Generalization       | ✔️         | ✔️     | ✔️ | ✔️     |
| Aggregation          | ✔️         | ✔️     | ✔️ | ✔️     |

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
Cybersecurity Department – BLC
