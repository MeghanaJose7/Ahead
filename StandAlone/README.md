# SQL Query Receiver for OpenTelemetry Collector

## Overview

The SQL Query Receiver in OpenTelemetry Collector allows you to generate metrics from a database using custom SQL queries. This guide outlines the steps to deploy and configure the SQL Query Receiver.

### Stability

Metrics (Alpha)

## Prerequisites

- OpenTelemetry Collector installed and configured.
- Access to a supported database (PostgreSQL, MySQL, Snowflake, SQL Server, SAP HANA, Oracle DB).

## Installation

Install the SQL Query Receiver via Helm:

```bash
helm install sqlquery-receiver open-telemetry/opentelemetry-collector --values sql-metric-receiver.yaml
```
Ensure to replace sql-metric-receiver.yaml with your actual configuration file.

## Configuration
### Top-Level Fields
#### driver (required): 
Database driver name (postgres, mysql, snowflake, sqlserver, hdb, oracle).
datasource (required): Connection string for the database.
#### queries (required): 
List of SQL queries with metrics and logs configuration.
#### collection_interval (optional): 
Interval between query executions (default: 10s).
#### storage (optional): 
ID of a storage extension to track results.
telemetry (optional): Settings for component's telemetry.

## Metrics Queries
Each metrics section includes:

- metric_name (required)
- value_column (required)
- attribute_columns (optional)
- data_type (optional)
- value_type (optional)
- monotonic (optional)
- aggregation (optional)
- description (optional)
- unit (optional)
- static_attributes (optional)
- start_ts_column (optional)
- ts_column (optional)

Refer to driver-specific documentation for case-sensitivity and query details.

## Telemetry Logs
**telemetry.logs.query (optional):**
Logs query details when set to true.
