# US Capital Market Liquidity: ELT & Analytical Framework

Quantitative evaluation of US capital market liquidity dynamics is critical to modeling broader global financial market outcomes. This repository provides an automated Extract-Load-Transform (ELT) pipeline and data-management framework engineered for high-throughput, low-latency downstream analysis of large-scale financial datasets.

## System Architecture

The framework decouples storage from compute using an Apache Arrow-native local stack, optimizing for memory efficiency and vectorized execution:

1. **Ingestion & Data Management (DuckDB):** Executes raw data extraction, batch updates, strict schema enforcement, and SQL-based transformation workflows.
2. **Storage Layer (Apache Parquet):** Persists structured data in a local, partitioned Parquet data lake, balancing columnar scan performance, compression efficiency, and directory readability.
3. **Analytical Engine (Polars):** Powers native and user-defined downstream quantitative pipelines via lazy evaluation and multi-threaded vectorized query execution.

## Core Capabilities

* **Automated ELT & Batch Compaction:** Streamlines historical backfills and incremental daily updates while maintaining optimal Parquet row-group sizing.
* **Deterministic Schema Enforcement:** Validates incoming market data structures against strict type definitions prior to lake commitment to prevent silent downstream corruption.
* **Zero-Copy Interoperability:** Leverages Apache Arrow memory buffers to pass datasets seamlessly between DuckDB SQL workflows and Polars DataFrame/LazyFrame pipelines without serialization overhead.
