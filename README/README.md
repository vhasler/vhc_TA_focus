# FinOps App for FOCUS™ (Cost and Usage)

FinOps Cost and Usage over FOCUS™ Specification.  
The unifying format for cloud billing data.

---

## Author
**Ing. Victor Hasler, MSc.**  
[Victor Hasler @ FullStacks GmbH](mailto:victor.hasler@fullstacks.eu)

---

## Overview

Sourcetypes: 
focus:json      - Standard sourcetype for json formated file ingestions
focus:csv       - Standard sourcetype for manuall csv file ingestions 
azure:focus:csv - for Azure ingestion automatic split in --> azure:focus:csv:v10r2 (FOCUS version 1.1) || azure:focus:csv:v12 (FOCUS version 1.2)

This app provides:

- **Data Models**
  - `focus`
- **Sample Data**
  - CSV files
  - `eventgen.conf`
- **Dashboards**
  - **FinOps**
    - Management (default)
    - Analyze Dashboard
    - Report Dashboard
  - **FRAMEWORK**
    - FinOps Framework
    - FinOps Principles
    - FinOps Capabilities Domains
    - FinOps Capabilities Personas Cases
    - FinOps Use Cases

It supports hybrid data ingestion:
- CSV ingestion via Splunk file monitoring (`monitor://`)
- JSON ingestion via HEC (`services/collector/event`)

---

## Splunk Setup

- **Index Macro:**  
  `Settings → Advanced Search → Search Macros` → define your index (default: `focus_sample`)
  
- **Sourcetypes:**  
  `Settings → Source Types` → `focus:csv` and `focus:json` are included in this app.

---

## Splunk Setup (Sample Environment)

- **Index:**  
  `Settings → Indexes → New Index` → create `focus_sample`
  
  ➡️ In Splunk Cloud you may need to create a production index named `focus`.

- **Sourcetype:**  
  - `focus:csv` 
  - `focus:json`

---

## Dependencies

- [SA-Eventgen](https://splunkbase.splunk.com/app/1924)  
  *(for event simulation / sample data generation)*

**Important:**  
Every Splunk restart triggers SA-Eventgen to simulate events!  
To prevent unwanted data generation after first start, set:
```bash
disabled = true 
```
in your eventgen.conf.

---

### Splunk Deployment Matrix (onPrem)

| Splunk Role         | Required |
| ------------------- | -------- |
| Search Head         | ✅ Yes   |
| Indexer             | ✅ Yes   |
| Heavy Forwarder     | ❌ No    |
| Universal Forwarder | ❌ No    |

### Splunk Deployment Matrix (cloud)

| Splunk Role         | Required |
| ------------------- | -------- |
| Cloud Stack         | ✅ Yes   |
| Heavy Forwarder     | ❌ No    |
| Universal Forwarder | ❌ No    |

---
## Licensing
- The underlying open-source components are licensed under the MIT License (see LICENSE.txt).
- The full app (FinOps App for FOCUS™) is proprietary to Ing. Victor Hasler MSc. (see TERMS.txt).
---
## Maintenance

This app can be modified and maintained by:
- Ing. Victor Hasler, MSc.