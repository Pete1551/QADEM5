# Architecture Decision Record
ADR-001: Pipeline Architecture
Date: 27/07/2026

Status: Accepted

Context
We need to process data from four sources (CSV, JSON, text, Excel) for Newham Public Library. The data has quality issues and needs to be cleaned before it can be used for analysis.

Decision
We will use a medallion architecture with three layers:

Bronze - raw data ingested exactly as received
Silver - cleaned and validated data
Gold - analysis-ready aggregations



Reasons
This provides clear, separate lineage enabling easier troubleshooting and separation of responsibilities for each layer
Consequences
Raw data is always preserved in bronze - we can reprocess if cleaning logic changes
Silver is the trust boundary - gold always reads from silver, never bronze
(add any other consequences you can think of)
