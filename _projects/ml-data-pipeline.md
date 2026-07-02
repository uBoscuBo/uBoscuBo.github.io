<!-- Code Example -->

---
layout: project
title: "High-Throughput ML Data Pipeline"
description: >-
  A modular async Python pipeline for ingesting, featurizing, and versioning
  large molecular datasets (10M+ compounds) to support ML model training at scale.
tags: [Python, FastAPI, PostgreSQL, Docker, MLOps]
date: 2022-08-15
github: "https://github.com/yourusername/mol-pipeline"
demo: ""
paper: ""
image: ""
featured: false
status: "completed"
published: false
---

## Overview

Training high-quality molecular ML models requires clean, consistent, and
versioned data. This project provides an end-to-end pipeline that pulls
compounds from public databases (PubChem, ChEMBL), featurizes them with
RDKit, and stores them in a versioned PostgreSQL schema.

## Architecture

```
PubChem API ──┐
ChEMBL API  ──┤──► Ingestion Workers ──► Feature Store ──► Training Interface
Custom CSV  ──┘        (async Python)     (PostgreSQL)       (PyTorch Dataset)
```

### Key Components

- **Ingestion layer**: Async workers using `aiohttp` + `asyncio.Queue`
- **Featurization**: Morgan fingerprints, ECFP, graph descriptors via RDKit
- **Storage**: Versioned schema with `dataset_version` table for reproducibility
- **API**: FastAPI endpoints for querying and downloading splits

## Performance

| Throughput | Value |
|------------|-------|
| Ingestion  | ~50k compounds/min |
| Featurization | ~200k fingerprints/min |
| Storage    | ~30 GB / 10M compounds |

## Running Locally

```bash
docker compose up -d
python pipeline/ingest.py --source pubchem --limit 10000
python pipeline/featurize.py --version v1.0
```
