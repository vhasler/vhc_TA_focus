# TA FOCUS™ (Cost and Usage)

Cost and Usage by FOCUS™ Specification.  
The unifying format for cloud billing data.

## Installation
**Set your INDEX (e.g. focus, finops, cost ...) manually either onPrem or in an cloud environment, for better maintainace**
- define your choosen index in the `focus_index` macro 

`Settings → Advanced Search → Search Macros` → insert your defined index (default: `index=finops OR index=focus OR index=focus_sample`)

**Set your SOURCETYPE**
- `focus:json`      - Standard sourcetype for json-formatted file ingestions
- `focus:csv`       - Standard sourcetype for csv-formatted file ingestions 
- `azure:focus:csv` - for Azure ingestion automatic split in `azure:focus:csv:v10r2` (FOCUS version 1.1) OR `azure:focus:csv:v12` (FOCUS version 1.2)

`Settings → Source Types`

It supports:
- CSV ingestion via Splunk file monitoring (`monitor://`)
- JSON ingestion via HEC (`services/collector/event`)
- AZURE ingestion via Splunk Add-on for Microsoft Cloud Services

**DATAMODEL** `focus` supports following FOCUS Versions:
- v1.0
- v1.1
- v1.2

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

### Dependencies
- [Splunk Add-on for Microsoft Cloud Services](https://splunkbase.splunk.com/app/3110)
  *(for Azure Storage Account connection)*

- [vhc_SA_cloudregions](https://github.com/vhasler/vhc_SA_cloudregions)
  *(provides a lookup for regions_id)*

- [SA-Eventgen](https://splunkbase.splunk.com/app/1924)  
  *(for event simulation / sample data generation)*

---

## Ingest Sample Data
Sample data are stored in the `samples` folder and uses the csv file `focus_sample_100000.sample`
For the first run set up your **INDEX** under `Settings → Indexes → New Index` → choose `focus_sample`

**IMPORTANT** every splunk restart triggers the SA-Eventgen to ingest the file again.  
To prevent unwanted data generation or multiple data ingestions set in `eventgen.conf`:
```bash
# Default "true" if you want generate sample data set it to "false" and restart splunk 
disabled = true 
```

---

## Licensing
- The underlying open-source components are licensed under the MIT License (see LICENSE.txt).
- The full app (FinOps App for FOCUS™) is proprietary to Ing. Victor Hasler MSc. (see TERMS.txt).


### Author/Maintenance
Ing. Victor Hasler, MSc.