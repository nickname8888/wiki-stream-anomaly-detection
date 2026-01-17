# Wiki Stream Anomaly Detection

A real-time streaming system that monitors live edit activity
on English Wikipedia and detects abnormal behavior indicative of breaking events,
content disputes, or sudden public attention.

The system is designed as a distributed pipeline using streaming-first principles,
with clear separation between ingestion, processing, anomaly scoring, and serving.

## Problem Statement
Wikipedia reacts rapidly to real-world events. Sudden spikes or unusual patterns
in page edit activity often precede or accompany breaking news. Raw edit streams,
however, are noisy and difficult to interpret.

This project converts raw Wikipedia edit events into structured, interpretable
anomaly signals in real time.

## High-Level Architecture
- Ingestion service consumes Wikipedia RecentChanges SSE
- Events are normalized and published to Kafka
- Spark Structured Streaming performs windowed aggregation and online anomaly scoring
- Detected anomalies are persisted and exported as snapshots
- A lightweight serving layer exposes results via a read-only API

## Key Characteristics
- Real-time, unbounded data stream
- Best-effort ingestion with late and missing events
- Online statistical anomaly detection (no offline training)
- Compute and serving layers are decoupled

## Tech Stack
- Python
- Kafka
- Spark Structured Streaming (PySpark)
- PostgreSQL
- Docker
- FastAPI

## Status
Initialization setup being configured. 
