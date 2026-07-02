Day-by-day execution blueprint for **Month 1 (July 2026)**. This curriculum is engineered to transition you from writing high-level "AWS Glue wrapper scripts" to architecting high-performance, predictable distributed compute infrastructure.

---

## 🗓️ Week 1: Spark Core Architecture & Execution Mechanics

**Daily Commitment:** 2 hours (Weekdays) | 4 hours (Weekends)
**Focus:** Understanding the physical reality of distributed clusters and breaking down execution graphs.

### Day 1: Master-Worker Topology Deep Dive

* **Time Allocation:** 2 Hours
* **Concepts:** Driver JVM vs. Executor JVM, Cluster Managers (Standalone, YARN, Kubernetes coordination), resource allocation loops.
* **Reading:** *Spark Architecture: Master–Worker Model* (Data Lakehouse Hub Expert Guide).
* **Video:** "Spark Architecture & Cluster Topology Deep Dive" (FreeCodeCamp / TechWithTim Data series or Apache Spark official channel architecture playlists).

### Day 2: The Lineage Graph & Lazy Evaluation

* **Time Allocation:** 2 Hours
* **Concepts:** Logical vs. Physical DAG (Directed Acyclic Graph), Narrow vs. Wide dependencies, RDD immutability, lineage recomputation mechanics during node failure.
* **Reading:** *Core Data Structures: RDDs to DataFrames* (Datalakehouse Hub / Databricks documentation).
* **Video:** "Apache Spark Internals: Transformations vs Actions" (Data Vidhya / Databricks University).

### Day 3: Deconstructing Jobs, Stages, and Tasks

* **Time Allocation:** 2 Hours
* **Concepts:** What defines a Job boundary (Actions)? What defines a Stage boundary (Shuffle/ShuffleExchange)? Task scheduling and execution slots per core.
* **Reading:** *The Execution Model: Driver, Executors, Jobs, Stages, Tasks* (Data Vidhya).
* **Video:** "Understanding Spark Stages and Tasks" (Advancing Analytics YouTube channel).

### Day 4: Anatomy of a Shuffle Operations

* **Time Allocation:** 2 Hours
* **Concepts:** Map-side vs. Reduce-side shuffle files, disk serialization, network I/O, hash partitioning basics. Why shuffle is the #1 performance killer.
* **Reading:** *What Happens During a Shuffle* (Data Vidhya).
* **Video:** "Spark Shuffle Mechanics Explained" (Rock the JVM / Jacek Laskowski talks).

### Day 5: Introduction to local Sandboxing via Docker

* **Time Allocation:** 2 Hours
* **Concepts:** Containerizing a standalone Spark cluster, configuring a multi-worker setup locally, exposing ports `4040` (Spark UI) and `8080` (Master UI).
* **Reading/Code:** *Dockerizing a Spark Cluster* (GitHub repositories / dev.to guides).
* **Action:** Write a basic `docker-compose.yml` spinning up 1 Spark Master and 2 Spark Workers.

### Day 6 & 7 (Weekend): LeetCode & Basic System Design Core

* **Time Allocation:** 4 Hours per day
* **LeetCode Sprints:** Solve 4 problems on Arrays & Hashing (e.g., *Two Sum*, *Contains Duplicate*, *Valid Anagram*, *Group Anagrams*).
* **System Design:** Study Storage Engine Internals. Deep dive into B-Trees vs. LSM (Log-Structured Merge) Trees. Understand why LSM-Trees are optimized for write-heavy storage.
* **Reading:** *Designing Data-Intensive Applications* (Martin Kleppmann), Chapter 3 (Storage and Retrieval).

---

## 🗓️ Week 2: JVM Internals, Memory Management & Tuning

**Daily Commitment:** 2 hours (Weekdays) | 4 hours (Weekends)
**Focus:** Eradicating Out-Of-Memory (OOM) errors by masterfully managing the Executor Heap.

### Day 8: Executor JVM Memory Topology

* **Time Allocation:** 2 Hours
* **Concepts:** Breaking down Heap allocation: Reserved Memory (300MB fixed), User Memory, and Spark Memory.
* **Reading:** *Spark memory tuning на собеседовании Data Engineer* (Kariernik / Spark Docs).

### Day 9: Execution vs. Storage Fractions

* **Time Allocation:** 2 Hours
* **Concepts:** Tuning `spark.memory.fraction` (default 0.6) and `spark.memory.storageFraction` (default 0.5). Eviction mechanics: how Execution reclaims space from Storage dynamically.
* **Reading:** *Unified Memory Model Specification* (Apache Spark Documentation).
* **Video:** "Deep Dive: Memory Management in Apache Spark" (Databricks Spark Summit Archive).

### Day 10: Off-Heap Memory & Overhead Allocation

* **Time Allocation:** 2 Hours
* **Concepts:** Tuning `spark.executor.memoryOverhead` (container memory overhead) vs. `spark.memory.offHeap.size`. Understanding container termination via YARN/K8s due to memory leaks.
* **Reading:** *How to Tune Spark Memory and Executor Settings* (OneUptime Blog).

### Day 11: Garbage Collection (GC) in Spark

* **Time Allocation:** 2 Hours
* **Concepts:** Young Generation vs. Old Generation heaps. Diagnosing high GC pauses via logs or Spark UI. Tuning flags like `-XX:+UseG1GC`.
* **Reading:** *ATuMm: Auto-tuning Memory Manager in Apache Spark* (ResearchGate / DataFlair Tuning Guide).
* **Video:** "Tuning Garbage Collection in Apache Spark" (Databricks Tech Talks).

### Day 12: Py4J Bridges & Serialization Overhead

* **Time Allocation:** 2 Hours
* **Concepts:** The Py4J Gateway architecture. The hidden cost of serializing JVM objects to Python worker processes and back. Why raw Python UDFs break everything.
* **Reading:** *The Overhead of Python UDFs in PySpark* (Medium - Tech engineering blogs).
* **Video:** "PySpark Internals & Why Python UDFs are Slow" (Databricks / PyData).

### Day 13 & 14 (Weekend): Memory Configuration Calculations & LeetCode

* **Time Allocation:** 4 Hours per day
* **Calculations Practice:** Given an EC2 node with 8 vCPUs and 32GB RAM, calculate optimal `spark.executor.instances`, `spark.executor.cores`, and `spark.executor.memory` ensuring 1 core is spared for OS/YARN daemon overhead.
* **LeetCode Sprints:** Solve 4 problems on Two-Pointer patterns (e.g., *Valid Palindrome*, *Two Sum II*, *3Sum*, *Container With Most Water*).

---

## 🗓️ Week 3: The Catalyst Optimizer, Project Tungsten & AQE

**Daily Commitment:** 2 hours (Weekdays) | 4 hours (Weekends)
**Focus:** Knowing exactly how Spark translates declarative SQL/DataFrames into binary execution.

### Day 15: The Four Phases of Catalyst

* **Time Allocation:** 2 Hours
* **Concepts:** Unresolved Logical Plan ➡️ Analysis via Catalog ➡️ Optimized Logical Plan ➡️ Physical Plan selections.
* **Reading:** *Catalyst Optimizer in Spark Explained* (Spark Playground).
* **Video:** "Deep Dive Into Catalyst: The Brain of Spark SQL" (Databricks Spark Summit).

### Day 16: Reading Execution Plans Programmatically

* **Time Allocation:** 2 Hours
* **Concepts:** Mastering `.explain(mode="extended")` and `.explain(mode="formatted")`. Spotting Predicate Pushdown, Column Pruning, and Exchange operators.
* **Reading:** *Apache Spark: The Complete Deep Dive* (Aman Nandan, Jun 2026).

### Day 17: Project Tungsten Unveiled

* **Time Allocation:** 2 Hours
* **Concepts:** Bypassing JVM overhead via `sun.misc.Unsafe`. Off-heap binary memory layouts that minimize Object Headers. CPU cache-aware computing.
* **Reading:** *Project Tungsten: The Hardware Performance Layer* (Medium / Data Vidhya).
* **Video:** "Project Tungsten: Bringing Spark Closer to Bare Metal" (Josh Rosen / Databricks).

### Day 18: Whole-Stage Code Generation (WSCG)

* **Time Allocation:** 2 Hours
* **Concepts:** Eliminating the Volcano Iterator model. How Spark compiles an entire processing stage into a single tight Java bytecode loop at runtime. Identifying `WholeStageCodegen` boxes in the Spark UI.
* **Reading:** *Spark SQL: Another 16x Faster After Tungsten* (Spark Summit talk breakdown).

### Day 19: Adaptive Query Execution (AQE) - Core Mechanics

* **Time Allocation:** 2 Hours
* **Concepts:** Runtime optimization via `spark.sql.adaptive.enabled`. Dynamically coalescing post-shuffle partitions to ensure optimal file sizes (targeting 128MB–200MB).
* **Reading:** *How to Tune Shuffle Partitions and AQE* (OneUptime).

### Day 20 & 21 (Weekend): Advanced AQE & System Design (Sharding)

* **Time Allocation:** 4 Hours per day
* **AQE Deep Dive:** Study dynamic join strategies (switching SortMergeJoin to BroadcastHashJoin at runtime) and dynamic skew join resolution.
* **System Design:** Master Database Sharding methodologies: Horizontal partitioning, hash-based vs range-based sharding, re-sharding challenges, and consistent hashing mechanics.
* **LeetCode Sprints:** Solve 3 problems on Two-Pointer/Sliding Window (e.g., *Best Time to Buy and Sell Stock*, *Longest Substring Without Repeating Characters*).

---

## 🗓️ Week 22-28: Data Skew, Custom Partitioning & Capstone Project

**Daily Commitment:** 2 hours (Weekdays) | 4 hours (Weekends)
**Focus:** Building an elite-level portfolio piece processing structural data anomalies.

### Day 22: Data Skew Diagnosis & Salting Keys

* **Time Allocation:** 2 Hours
* **Concepts:** Identifying straggling tasks in the Spark UI. The mathematics of Key Salting: appending random suffixes to skewed keys to evenly distribute data across executors, then cleaning suffixes post-join.
* **Reading:** *Handling Data Skew in Spark: Salting and Broadcast Strategies* (Databricks Architecture Blog).

### Day 23: Custom Partitioners & Partitions Optimization

* **Time Allocation:** 2 Hours
* **Concepts:** Subclassing `pyspark.rdd.Partitioner` or implementing custom partitioning columns using structural hashes. Forcing predictable cluster routing.
* **Code:** Prototype a basic custom string-hashed partitioner.

### Days 24 to 28: Capstone Portfolio Project Construction

* **Time Allocation:** 2 Hours/day (Weekdays) + 4 Hours/day (Weekend)
* **The Mission:** Write a complete Python system running on your local multi-node Docker cluster.
* **Project Checklist:**
1. Generate a mock 500 GB telemetry clickstream dataset where 70% of the events share a single malicious/highly active corporate IP address (severe skew).
2. Write an optimized PySpark transformation pipeline that reads this dataset.
3. Implement a **Salted Join Strategy** to join this clickstream against a localized Metadata IP lookup table.
4. Profile the application via the local Spark UI (`localhost:4040`). Take screenshots showing uniform executor memory allocation and balanced runtime execution across all tasks.
5. Cleanly check in the codebase with a polished, professional `README.md` containing performance comparison charts (Unsalted vs. Salted execution timelines).



---

## 🗓️ Week 29-31: Certification, Resume Engineering & Outbound Launch

**Daily Commitment:** 2 hours

### Day 29: Databricks Certified Data Engineer Associate Sprint

* **Time Allocation:** 2 Hours
* **Focus:** Take practice exams covering Lakehouse architecture, fundamental Delta Lake transformations, and basic Spark SQL syntax. Knock out the certification.

### Day 30: High-Impact Resume & LinkedIn Refactoring

* **Time Allocation:** 2 Hours
* **Action Plan:** Remove descriptions like *"Built Glue pipelines to move data to Redshift"*. Replace with:
> *"Architected local multi-node distributed test sandboxes via Docker-Compose. Engineered automated key-salting strategies in PySpark that reduced execution skew by 4x, optimizing shuffle write allocations across multi-node execution stages."*


* **LinkedIn Action:** Write a brief technical post breaking down how Project Tungsten uses off-heap binary structures to minimize JVM Garbage Collection pressure.

### Day 31: Outbound Networking Launch

* **Time Allocation:** 2 Hours
* **Targeting:** Source 10 Senior Data Platform Engineers/Engineering Managers at Tier-1 product firms in Bangalore or Hyderabad (e.g., Uber, DoorDash, Swiggy, Flipkart).
* **Outbound Script:** Reach out directly via LinkedIn with high signal:
> *"Hey [Name], built a local multi-node Spark cluster simulation solving major clickstream data skews via custom metadata-driven salting strategies. I noticed your team manages high-throughput platforms. Would love to swap notes on memory fraction tuning over message."*



---

## 🛠️ Unified Study Tracker & Resources

| Category | High-Signal Reference Material | Core Takeaway |
| --- | --- | --- |
| **Text Reading** | *Apache Spark Internals: Catalyst, Tungsten & Shuffle Performance* (Data Vidhya)<br>

<br>

<br>*Spark memory tuning на собеседовании Data Engineer* (Kariernik) | Understand the low-level physical layout of how data resides off-heap and inside bytecode stages. |
| **Video Playlists** | **Advancing Analytics** (Spark UI & Architecture)<br>

<br>

<br>**Rock the JVM** (Spark Advanced Internals) | Learn to decode visual DAG graphs in the Spark UI to spot real-time shuffles instantly. |
| **Local Sandbox** | Docker Compose with `bitnami/spark:latest` images | Eliminate cloud costs by running localized multi-node master/worker clusters locally. |
