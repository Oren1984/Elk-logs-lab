# ELK Logs Lab

Minimal ELK lab for ingesting demo events into `student_logs` and exploring them in Kibana.

---

## Overview

A simple, ready-to-run ELK setup for practicing log ingestion, basic searches, and Kibana visualizations with demo data.

---

## Tech Stack

- Elasticsearch
- Kibana
- Docker Compose
- Bash
- curl

---

## Quick Start

```bash
docker compose up -d
curl -s http://localhost:9200/_cluster/health?pretty
```

### Generate demo data:

```bash
chmod +x scripts/generate_advanced_logs.sh
./scripts/generate_advanced_logs.sh
```

### Optional continuous stream:

```bash
chmod +x scripts/stream_logs.sh
./scripts/stream_logs.sh
```

---

## Usage

- Open Kibana: http://localhost:5601

- Create a Data View: student_logs*

- Select timestamp as the time field

- Explore logs, searches, and simple visualizations

Useful examples:

- Bar chart: actions / users

- Pie chart: products

- Metric: errors (status_code >= 400)

- Line chart: average duration_ms

Quick checks:

```bash
./scripts/curl-cheats.sh
```

---

## Cleanup

Reset data only:

```bash
curl -X DELETE http://localhost:9200/student_logs
```

Stop the stack:

```bash
docker compose down -v
```

---

## Notes

- Security is disabled for lab simplicity

- Built for learning and demo purposes

- Default values can be overridden with environment variables

Env vars:

- Generator: ES_URL, INDEX, COUNT

- Streamer: INDEX, INTERVAL

---

