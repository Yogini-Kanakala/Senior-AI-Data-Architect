Welcome to **Month 1** of your intensive transition into an elite **Data Platform and GenAI Infrastructure Engineer**.

To balance your demanding 9–10 hour workday with this aggressive upskilling tract, we will strictly enforce a structured routine: **2.5 hours on weekdays** (split into 45 minutes of algorithmic problem solving and 1 hour 45 minutes of systems engineering) and **6 hours on weekends** (focused purely on deep-dive coding, infrastructure deployments, and profiling).

---

## Month 1 Overview: JVM Internals & Advanced Distributed Processing

* **Dates**: May 25, 2026 – June 23, 2026
* **Primary Objective**: Transcend the "tool-user" PySpark barrier. You must master the internal JVM execution engine, Spark’s memory manager, serialization layers, and partition mechanics. This depth will prepare you to answer high-scale optimization questions during senior-level interviews at top-paying product companies.



---

## Week 1: Spark Core Architecture & Environment Setup (May 25 – May 31)

### Day 1 (Monday, May 25): Databricks Free Edition & Environment Setup

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Study the sliding window pattern. Solve([https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)) (Easy) using a Hash Set. Analyze its time and space complexity: $O(N)$ space and $O(N)$ time.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Get started on the Databricks Free Edition. Understand its serverless-only workspace, limits, and how it replaced the legacy Community Edition.
* **Action**: Create your account. Follow the instructions to bypass the paid enterprise trial.
* **Step-by-Step Setup**:
1. Navigate to the([https://www.databricks.com/try-databricks](https://www.databricks.com/try-databricks)).
2. Enter your details. Under "Work Email", you can use your personal email address.
3. On the next screen ("Choose a Cloud Provider"), do **not** select AWS, Azure, or GCP. Instead, look below the options and click on **Get Started with Free Edition** (previously known as Community Edition).
4. Solve the validation puzzle, check your email for the activation link, and log in to your new serverless workspace.




* **Day 1 Curated Resources**:
*([https://community.cloud.databricks.com/](https://community.cloud.databricks.com/))
*([https://docs.databricks.com/aws/en/getting-started/free-edition-limitations](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations))

---

### Day 2 (Tuesday, May 26): The Spark Distributed Runtime Model

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve [LeetCode 242: Valid Anagram](https://leetcode.com/problems/valid-anagram/) (Easy). Implement it with a single array-based hash map representing character counts to optimize execution speed over sorting.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master the core distributed computing primitives: Driver Program, Cluster Manager (YARN, Kubernetes, Standalone), Worker Nodes, Executors, and Tasks.
* **Action**: Sketch the network architecture of a Spark Application. Understand exactly how the Driver processes your Python/SQL code, builds a logical execution plan, and schedules tasks across worker nodes.


* **Day 2 Curated Resources**:
*([https://medium.com/@kaviprakash.2007/spark-and-databricks-fundamentals-and-architecture-in-this-article-we-will-deep-dive-into-the-fundamentals-of-spark-databricks-and-its-architecture-types-of-databricks-clusters-in-detail-a-clap-icon-73-b57280a8260](https://medium.com/@kaviprakash.2007/spark-and-databricks-fundamentals-and-architecture-in-this-article-we-will-deep-dive-into-the-fundamentals-of-spark-databricks-and-its-architecture-types-of-databricks-clusters-in-detail-a-clap-icon-73-b57280a8260))
*([https://spark.apache.org/docs/latest/cluster-overview.html](https://spark.apache.org/docs/latest/cluster-overview.html))

---

### Day 3 (Wednesday, May 27): The JVM Memory Model & Memory Pools

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)) (Easy). Implement the $O(N)$ single-pass hash map solution. Explain why returning indices is faster than a nested loop.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master Spark's internal JVM Executor Memory layout. Understand how Spark divides JVM heap memory into **Execution**, **Storage**, **User**, and **Reserved** memory fractions.
* **Mathematical Layout**:
Let $M$ represent the total JVM Heap allocated to an Executor, and $R$ represent the Reserved Memory (hardcoded to $300\text{ MB}$ inside Spark to safeguard against Out-of-Memory errors). The usable memory space is defined as:

$$M_{\text{usable}} = M - 300\text{ MB}$$



By default, Spark allocates $60\%$ of $M_{\text{usable}}$ as unified memory managed by the `MemoryManager` (`spark.memory.fraction = 0.6`). This space is dynamically shared between:
* **Execution Memory** ($60\%$ of unified memory by default): Used for shuffles, joins, sorts, and aggregations.
* **Storage Memory** ($40\%$ of unified memory by default): Used for caching user dataframes and broadcast objects.
The remaining $40\%$ of $M_{\text{usable}}$ is allocated to **User Memory** for storing custom objects and user-defined functions (UDFs).




* **Day 3 Curated Resources**:
*([https://www.databricks.com/blog/what-is-spark-tuning](https://www.databricks.com/blog/what-is-spark-tuning))
*([https://spark.apache.org/docs/latest/configuration.html#memory-management](https://spark.apache.org/docs/latest/configuration.html#memory-management))

---

### Day 4 (Thursday, May 28): RDDs vs. DataFrames & Performance Abstractions

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve [LeetCode 49: Group Anagrams](https://leetcode.com/problems/group-anagrams/) (Medium). Use a tuple of character frequencies as the hash key to avoid string sorting overhead.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Analyze the performance shift from low-level Resilient Distributed Datasets (RDDs) to high-level DataFrames.


* **Action**: Explain why raw Python RDD transformations are notoriously slow due to JVM-to-Python socket serialization overhead. Contrast this with the Structured APIs (DataFrames, SQL) which generate bytecode executed directly on the JVM, completely bypassing Python execution overhead.


* **Day 4 Curated Resources**:
*([https://www.datacamp.com/blog/pyspark-interview-questions](https://www.datacamp.com/blog/pyspark-interview-questions)) 
*([https://spark.apache.org/docs/latest/sql-programming-guide.html](https://spark.apache.org/docs/latest/sql-programming-guide.html))



---

### Day 5 (Friday, May 29): Lazy Evaluation & The Catalyst Logical Plan

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)) (Medium). Solve using Bucket Sort to achieve an optimal $O(N)$ execution path, bypassing the standard $O(N \log K)$ Heap approach.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master lazy evaluation, DAG (Directed Acyclic Graph) creation, and Spark's compilation stages: **Unresolved Logical Plan** -> **Analyzed Logical Plan** -> **Optimized Logical Plan** -> **Physical Plan**.
* **Action**: Write a PySpark script with basic filter and project transformations. Run `.explain(True)` to print and analyze the four compilation phases.


* **Day 5 Curated Resources**:
*([https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260](https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260))
*([https://www.bosscoderacademy.com/blog/top-40-pyspark-interview-questions](https://www.bosscoderacademy.com/blog/top-40-pyspark-interview-questions)) 



---

### Day 6 (Saturday, May 30): Weekend Deep-Dive – Local Multi-Node Cluster Construction

* **Time Allocation**: 6 Hours
* **Weekend Coding (4 Hours)**:
* Clone the([https://github.com/MarlonRibunal/learning-data-engineering](https://github.com/MarlonRibunal/learning-data-engineering)) to dissect real-world production configurations.


* Write a local `docker-compose.yml` that provisions a three-tier local Spark Standalone Cluster:
* 1 Master Node (`spark-master`)
* 2 Worker Nodes (`spark-worker-1`, `spark-worker-2`)
* A Jupyter/PySpark client container.




* Write a basic PySpark script to verify the cluster, access the local Spark UI (usually on port `8080`), and visually inspect the execution timeline.


* **System Design & Profiling (2 Hours)**:
* **Architecture Focus**: Study the CAP Theorem and consistent hashing in distributed filesystems. Draw an architecture map showing exactly how data blocks are replicated across disk nodes.




* **Day 6 Curated Resources**:
*([https://github.com/MarlonRibunal/learning-data-engineering](https://github.com/MarlonRibunal/learning-data-engineering)) 
*([https://github.com/afaqueahmad7117/spark-experiments](https://github.com/afaqueahmad7117/spark-experiments))



---

### Day 7 (Sunday, May 31): Weekend Deep-Dive – Parsing Schema Inconsistencies

* **Time Allocation**: 6 Hours
* **Weekend Ingestions (4 Hours)**:
* Write an end-to-end Python parser that reads messy, deeply nested, multi-format e-commerce clickstream payloads (JSON and CSV files).
* Explicitly define a custom, strict schema in PySpark using `StructType` and `StructField` rather than using `inferSchema=True`. Compare the Spark performance logs between the two runs to prove the metadata overhead savings.




* **Blogging & Branding (2 Hours)**:
* Write a technical walk-through on Medium or Dev.to explaining: *"Why using `inferSchema=True` in production Spark jobs is a costly architectural anti-pattern"*.




* **Day 7 Curated Resources**:
*([https://thedataforge.medium.com/30-data-engineering-interview-questions-kafka-and-pyspark-86a4712c8690](https://thedataforge.medium.com/30-data-engineering-interview-questions-kafka-and-pyspark-86a4712c8690)) 
*([https://selectstarsql.com/](https://selectstarsql.com/)) 



---

## Week 2: Wide vs. Narrow, Shuffling, and Partitioning (June 1 – June 7)

### Day 8 (Monday, June 1): Execution Mechanics – Narrow Transformations

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)) (Medium) with $O(1)$ auxiliary space complexity by using a running prefix-suffix multiplication sweep.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master narrow transformations: `select()`, `filter()`, `withColumn()`, and `map()`.
* **Action**: Explain why narrow operations run in-memory within a single partition on a single executor without any network transfer or disk writes. This is called *pipelining*.




* **Day 8 Curated Resources**:
*([https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c](https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c))
*([https://gaurav98095.medium.com/interview-questions-on-spark-optimizations-917e8c81256b](https://gaurav98095.medium.com/interview-questions-on-spark-optimizations-917e8c81256b)) 



---

### Day 9 (Tuesday, June 2): Execution Mechanics – Wide Transformations

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/valid-sudoku/](https://leetcode.com/problems/valid-sudoku/)) (Medium) using array hashing matrices.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master wide transformations: `groupBy()`, `join()`, `distinct()`, and `repartition()`.
* **Action**: Understand exactly why wide operations force a **shuffle**—requiring Spark to serialize data, write it to local disk, and transfer it over the network so matching keys are grouped onto the same executor.


* **Day 9 Curated Resources**:
*([https://www.bosscoderacademy.com/blog/top-40-pyspark-interview-questions](https://www.bosscoderacademy.com/blog/top-40-pyspark-interview-questions)) 
*([https://thedataforge.medium.com/30-data-engineering-interview-questions-kafka-and-pyspark-86a4712c8690](https://thedataforge.medium.com/30-data-engineering-interview-questions-kafka-and-pyspark-86a4712c8690)) 



---

### Day 10 (Wednesday, June 3): Partitioning Strategies – Control vs. Chaos

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)) (Medium) in strict $O(N)$ time by storing elements in a hash set and querying neighbors only if the current value is the start of a sequence.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master partitioning strategies: HDFS block sizing, Spark default parallelism, and custom data partitions.
* **Calculation**:
How does Spark calculate the initial execution partition count? It defaults to reading one partition per contiguous file block on disk (default is $128\text{ MB}$ in standard modern storage). The target partition count during shuffles is controlled by:
`spark.sql.shuffle.partitions` (which defaults to 200).
You must learn to scale this programmatically:

$$\text{Target Shuffle Partitions} = \frac{\text{Total Input Size}}{128\text{ MB}} \times 3$$




* **Day 10 Curated Resources**:
*([https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260](https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260))
*([https://thedataforge.medium.com/roadmap-to-becoming-a-data-engineer-in-2026-56810ecae966](https://thedataforge.medium.com/roadmap-to-becoming-a-data-engineer-in-2026-56810ecae966)) 



---

### Day 11 (Thursday, June 4): Controlling File Distributions – Repartition vs. Coalesce

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Study the two-pointer technique. Solve [LeetCode 125: Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) (Easy) using a space-optimized two-pointer scan.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Differentiate `repartition()` from `coalesce()`.
* **Action**: Write a PySpark script that shrinks partition size. Run it once with `.repartition(2)` and once with `.coalesce(2)`. Dissect the Spark UI logs to prove that `repartition` triggers a massive wide shuffle while `coalesce` only merges contiguous partitions locally without shuffing.


* **Day 11 Curated Resources**:
*([https://www.datacamp.com/blog/pyspark-interview-questions](https://www.datacamp.com/blog/pyspark-interview-questions)) 
*([https://github.com/ankurchavda/SparkLearning/blob/master/advanced/optimizations.md](https://github.com/ankurchavda/SparkLearning/blob/master/advanced/optimizations.md))



---

### Day 12 (Friday, June 5): Storage Design – Columnar Parquet Mechanics

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)) (Medium) using an $O(1)$ space, two-pointer search.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Columnar vs. row-oriented storage formats (Parquet vs. CSV).
* **Action**: Read a $10\text{ GB}$ CSV file, write it as raw Parquet to local storage, and then run a selective column projection query on both. Measure and document the massive reduction in disk I/O and query runtime.


* **Day 12 Curated Resources**:
*([https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260](https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260))
*([https://www.interviewpilot.app/interview-guides/data-engineer](https://www.interviewpilot.app/interview-guides/data-engineer)) 



---

### Day 13 (Saturday, June 6): Weekend Deep-Dive – Profiling Shuffling Bottlenecks

* **Time Allocation**: 6 Hours
* **Weekend Coding (4 Hours)**:
* Ingest the([https://github.com/BauplanLabs/wap-with-bauplan-and-dbos](https://github.com/BauplanLabs/wap-with-bauplan-and-dbos)) (approx. $1\text{ GB}$) using your local Standalone Spark cluster.


* Write a poorly optimized PySpark ETL job that performs wide aggregations, filters after shuffles, and forces multiple redundant wide shuffles.
* Use your browser to access the Spark UI, inspect the **Stages** tab, record the total **Shuffle Read** and **Shuffle Write** sizes, and identify the exact line of code causing task-blocking stragglers.


* **System Design & Profiling (2 Hours)**:
* **SRE Focus**: Study SRE metrics for platform teams. Define SLOs (Service Level Objectives) and SLIs (Service Level Indicators) for high-throughput batch and streaming pipelines.


* **Day 13 Curated Resources**:
*([https://github.com/davidamom/snowflake-mcp](https://github.com/davidamom/snowflake-mcp)) 
*([https://www.reddit.com/r/dataengineeringjobs/comments/1qibmbi/data_engineer_interview_system_design/](https://www.reddit.com/r/dataengineeringjobs/comments/1qibmbi/data_engineer_interview_system_design/))



---

### Day 14 (Sunday, June 7): Weekend Deep-Dive – Portfolio Project 1 Architecture

* **Time Allocation**: 6 Hours
* **Weekend Architecting (4 Hours)**:
* Begin the complete technical blueprints for your first major portfolio project: **Real-Time Telemetry & Quality-of-Experience (QoE) Engine**.
* Map out the data lifecycle :


1. Ingestion: Raw telemetry JSON events from active OTT clients (buffering, latency, stream quality metrics) are sent to an HTTP endpoint.


2. Streaming: These events are processed in real-time.


3. Storage: High-throughput batch streaming into structured target tables.




* Draft the complete Entity Relationship Diagram (ERD), schema files, and partition paths for this real-time pipeline.




* **Resume Building (2 Hours)**:
* Re-write your professional resume to emphasize your OTT telemetry, analytics, and business impact. Convert passive lines like *"worked on QuickSight reports"* into active achievements: *"Designed an automated AWS Glue and Lambda ingestion pipeline handling $5\text{ TB}$ of raw telemetry data..."*.


* **Day 14 Curated Resources**:
*([https://medium.com/@tshraddhac/stop-building-random-projects-build-these-3-data-engineer-portfolio-projects-instead-0deb723eb80a](https://medium.com/@tshraddhac/stop-building-random-projects-build-these-3-data-engineer-portfolio-projects-instead-0deb723eb80a)) 
*([https://www.interviewpilot.app/interview-guides/data-engineer](https://www.interviewpilot.app/interview-guides/data-engineer)) 



---

## Week 3: Advanced Joins, Bucketing, and Skew Optimization (June 8 – June 14)

### Day 15 (Monday, June 8): Join Optimization – Broadcast Hash Joins

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)) (Medium) using sorting and an optimized two-pointer inner search loop.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master **Broadcast Hash Joins (BHJ)**.
* **Action**: Explain why broadcasting a small table (<10MB by default) to all executors avoids the expensive network shuffle step. Write a PySpark join code block using the `broadcast` hint:
```python
from pyspark.sql.functions import broadcast
df_joined = df_large.join(broadcast(df_small), "join_key")

```




* **Day 15 Curated Resources**:
*([https://thedataforge.medium.com/30-data-engineering-interview-questions-kafka-and-pyspark-86a4712c8690](https://thedataforge.medium.com/30-data-engineering-interview-questions-kafka-and-pyspark-86a4712c8690)) 
*([https://community.databricks.com/t5/community-articles/9-powerful-spark-optimization-techniques-in-databricks-with-real/td-p/132925](https://community.databricks.com/t5/community-articles/9-powerful-spark-optimization-techniques-in-databricks-with-real/td-p/132925))



---

### Day 16 (Tuesday, June 9): Join Optimization – Sort-Merge Joins (SMJ)

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)) (Medium) with an $O(N)$ two-pointer greedy convergence approach.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master **Sort-Merge Joins (SMJ)**.
* **Action**: Analyze Spark's default fallback join for large tables. Understand how the Sort-Merge join operates in three phases: shuffling keys across executors (Shuffle Phase), sorting keys within partitions (Sort Phase), and merging the sorted tables locally (Merge Phase).


* **Day 16 Curated Resources**:
*([https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260](https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260))
*([https://github.com/afaqueahmad7117/spark-experiments](https://github.com/afaqueahmad7117/spark-experiments))

---

### Day 17 (Wednesday, June 10): Resolving Data Skew – The Salting Pattern

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/longest-repeating-character-replacement/](https://leetcode.com/problems/longest-repeating-character-replacement/)) (Medium) using a sliding window.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master data skew resolution using the **Salting Pattern**.
* **Action**: Write a pure PySpark script that implements salting. If your join key is severely skewed, append a random integer (salt) to the key on the skewed table, and duplicate (explode) the smaller table to match all possible salt keys. This distributes skewed records evenly across partitions, preventing task bottlenecks.


* **Day 17 Curated Resources**:
*([https://www.cloudthat.com/resources/blog/handling-data-skew-in-spark-the-power-of-salting](https://www.cloudthat.com/resources/blog/handling-data-skew-in-spark-the-power-of-salting))
*([https://www.unraveldata.com/resources/databricks-data-skew-balance-partition-workloads](https://www.unraveldata.com/resources/databricks-data-skew-balance-partition-workloads))

---

### Day 18 (Thursday, June 11): Join Optimization – Bucketing vs. Partitioning

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/minimum-window-substring/](https://leetcode.com/problems/minimum-window-substring/)) (Hard) using an optimized sliding window with character validation frequencies.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Differentiate bucketing from partitioning.
* **Action**: Explain why partitioning creates physically isolated directory structures on disk (`partitionBy()`), while bucketing distributes data into a fixed number of hash-based files (`bucketBy()`). Bucketing is best for pre-shuffling tables on common join keys to prevent runtime shuffles.


* **Day 18 Curated Resources**:
*([https://blog.devgenius.io/spark-skew-handling-76759d9d7f6a](https://blog.devgenius.io/spark-skew-handling-76759d9d7f6a))
*([https://github.com/afaqueahmad7117/spark-experiments](https://github.com/afaqueahmad7117/spark-experiments))

---

### Day 19 (Friday, June 12): Handling Null Values Explicitly

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Study binary search. Solve([https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)) (Easy) in strict $O(\log N)$ time.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Null join keys causing severe data skew.
* **Action**: Explain why `NULL` values in a join key always map to the same partition during hashing, overloading a single executor. Write PySpark code to filter out or explicitly isolate `NULL` values before executing joins.


* **Day 19 Curated Resources**:
*([https://www.unraveldata.com/resources/databricks-data-skew-balance-partition-workloads](https://www.unraveldata.com/resources/databricks-data-skew-balance-partition-workloads))
*([https://www.datacamp.com/blog/pyspark-interview-questions](https://www.datacamp.com/blog/pyspark-interview-questions)) 



---

### Day 20 (Saturday, June 13): Weekend Deep-Dive – Salting Optimization Lab

* **Time Allocation**: 6 Hours
* **Weekend Coding (4 Hours)**:
* Write a fully executable PySpark script that joins a skewed $500\text{ GB}$ mock orders table (where $80\%$ of records share `customer_id = 9999`) with a smaller, balanced customers table.
* Salt the orders table with $5$ distinct buckets and expand the customers table to match.
* Run the salted join job, take a screenshot of your Spark execution timelines before and after optimization, and document the reduction in execution time.


* **System Design & Profiling (2 Hours)**:
* **Architecture Focus**: Review the Medallion (Bronze/Silver/Gold) Lakehouse Architecture. Define what business boundaries exist between raw logs (Bronze), cleaned dimensional models (Silver), and aggregated BI marts (Gold).




* **Day 20 Curated Resources**:
*([https://www.youtube.com/watch?v=TySeEpL3upE](https://www.youtube.com/watch?v=TySeEpL3upE)) 
*([https://medium.com/namaste-databricks/medallion-architecture-fact-dimension-table-design-in-databricks-30-a-clap-icon-30-a-response-icon-2-3c1308a0d24e](https://medium.com/namaste-databricks/medallion-architecture-fact-dimension-table-design-in-databricks-30-a-clap-icon-30-a-response-icon-2-3c1308a0d24e)) 



---

### Day 21 (Sunday, June 14): Weekend Deep-Dive – Portfolio Project 1 Data Generator

* **Time Allocation**: 6 Hours
* **Weekend Coding (4 Hours)**:
* Build a Python-based synthetic data generator that emits thousands of realistic client session JSON events (buffering, stream latency, session startup latency).
* Write the ingestion scripts inside your local Spark Standalone Cluster, verifying that the schema enforces clean type-casting, null handling, and partition path writing on disk.




* **Blogging & Branding (2 Hours)**:
* Write a technical blog post on Medium or Dev.to explaining: *"Mastering the Salting Technique in Spark: How to eliminate task-skew stragglers from your pipelines"*.


* **Day 21 Curated Resources**:
*([https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c](https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c))
*([https://github.com/jrlasak/awesome-databricks](https://github.com/jrlasak/awesome-databricks))

---

## Week 4: Caching, AQE, Spark UI Debugging, and Project Ingestion (June 15 – June 23)

### Day 22 (Monday, June 15): Cache vs. Persist Strategies

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/search-a-2d-matrix/](https://leetcode.com/problems/search-a-2d-matrix/)) (Medium) in strict $O(\log (M \times N))$ binary search time.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Differentiate `.cache()` from `.persist()`.


* **Action**: Explain why `.cache()` always stores data in-memory with `MEMORY_AND_DISK` storage level, while `.persist()` allows you to define custom storage tiers (such as `DISK_ONLY` or `MEMORY_ONLY_SER`). Always trigger caching with an active action (such as `.count()`).


* **Day 22 Curated Resources**:
*([https://community.databricks.com/t5/community-articles/9-powerful-spark-optimization-techniques-in-databricks-with-real/td-p/132925](https://community.databricks.com/t5/community-articles/9-powerful-spark-optimization-techniques-in-databricks-with-real/td-p/132925))
*([https://www.bosscoderacademy.com/blog/top-40-pyspark-interview-questions](https://www.bosscoderacademy.com/blog/top-40-pyspark-interview-questions)) 



---

### Day 23 (Tuesday, June 16): Adaptive Query Execution (AQE) Internals

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/koko-eating-bananas/](https://leetcode.com/problems/koko-eating-bananas/)) (Medium) using binary search.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master Adaptive Query Execution (AQE).
* **Action**: Study the three main pillars of AQE: dynamically coalescing shuffle partitions, dynamically switching join strategies (e.g., Sort-Merge to Broadcast Hash join), and dynamically optimizing skewed joins. Verify that `spark.sql.adaptive.enabled = true` is active in your Spark session configs.


* **Day 23 Curated Resources**:
*([https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260](https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260))
*([https://github.com/ankurchavda/SparkLearning/blob/master/advanced/optimizations.md](https://github.com/ankurchavda/SparkLearning/blob/master/advanced/optimizations.md))

---

### Day 24 (Wednesday, June 17): Garbage Collection (GC) Tuning & Serialization

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)) (Medium).


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Spark Garbage Collection and Kryo Serialization.
* **Action**: Explain why Java Serialization causes high garbage collection overhead and network latency. Configure Kryo Serialization in your Spark session and evaluate the performance gains:
```python
spark.conf.set("spark.serializer", "org.apache.spark.serializer.KryoSerializer")

```




* **Day 24 Curated Resources**:
*([https://www.databricks.com/blog/what-is-spark-tuning](https://www.databricks.com/blog/what-is-spark-tuning))
*([https://www.sprintzeal.com/blog/pyspark-interview-questions](https://www.sprintzeal.com/blog/pyspark-interview-questions)) 



---

### Day 25 (Thursday, June 18): Optimization Heuristics – Predicate Pushdown

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/time-based-key-value-store/](https://leetcode.com/problems/time-based-key-value-store/)) (Medium) using a dictionary of arrays optimized with binary search.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Master **Predicate Pushdown** and **Partition Pruning**.
* **Action**: Explain why Predicate Pushdown improves read performance by applying filters directly at the storage layers (such as Parquet/S3), completely avoiding loading unneeded columns and rows into memory.


* **Day 25 Curated Resources**:
*([https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260](https://medium.com/@kaviprakash.2007/spark-performance-optimization-in-databricks-a-complete-guide-ab57280a8260))
*([https://github.com/ankurchavda/SparkLearning/blob/master/advanced/optimizations.md](https://github.com/ankurchavda/SparkLearning/blob/master/advanced/optimizations.md))

---

### Day 26 (Friday, June 19): Spark UI Mastery – Thread Dumps & Spills

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Study stack-based patterns. Solve [LeetCode 20: Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) (Easy) in $O(N)$ time.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Debugging disk spills and executor thread blocks using the Spark UI.
* **Action**: Learn to read the Spark UI **Executors** and **Jobs** tabs to identify if data has spilled to disk due to executor memory limits. Recognize that disk spill is a performance bottleneck, signaling that you need to repartition the data or optimize memory allocation.


* **Day 26 Curated Resources**:
*([https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c](https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c))
*([https://medium.com/@nishchayagrawal/data-engineering-interview-questions-design-end-to-end-data-pipeline-02b21a883445](https://medium.com/@nishchayagrawal/data-engineering-interview-questions-design-end-to-end-data-pipeline-02b21a883445)) 



---

### Day 27 (Saturday, June 20): Weekend Deep-Dive – Profiling & Debugging Lab

* **Time Allocation**: 6 Hours
* **Weekend Coding (4 Hours)**:
* Force an Out-of-Memory (OOM) error on your local Spark Standalone Cluster by writing a query with a massive cross-join.
* Open the Spark UI, capture the exact trace, find the executor failure logs, and resolve the issue.
* Write down the specific diagnostic steps you took, creating an interview-ready playbook for OOM failures.


* **System Design & Profiling (2 Hours)**:
* **Architecture Focus**: Review a complete system design path for real-time telemetry pipelines: from client-side WebSDKs, through AWS API Gateways, into distributed log streams.




* **Day 27 Curated Resources**:
*([https://github.com/afaqueahmad7117/spark-experiments](https://github.com/afaqueahmad7117/spark-experiments))
*([https://www.startdataengineering.com/post/de_interview_sd/](https://www.startdataengineering.com/post/de_interview_sd/)) 



---

### Day 28 (Sunday, June 21): Weekend Deep-Dive – Portfolio Project 1 Spark Streaming

* **Time Allocation**: 6 Hours
* **Weekend Coding (4 Hours)**:
* Complete the PySpark Structured Streaming application for **Project 1 (QoE Ingestion Platform)**.


* Write the streaming execution code to read from your local generator, perform sliding window aggregations (e.g., measuring average buffering time per stream every 10 minutes), handle late-arriving records with watermarks, and write the outputs as optimized Parquet.


* **GitHub Optimization (2 Hours)**:
* Create a clean GitHub repository for Project 1. Write a comprehensive `README.md` containing the architecture diagram, local Docker execution commands, and schemas to prove your technical depth to recruiters.




* **Day 28 Curated Resources**:
*([https://dataengineeracademy.com/blog/data-engineer-portfolio-review-checklist-2026-what-hiring-managers-actually-score/](https://dataengineeracademy.com/blog/data-engineer-portfolio-review-checklist-2026-what-hiring-managers-actually-score/)) 
*([https://github.com/afaqueahmad7117/spark-experiments](https://github.com/afaqueahmad7117/spark-experiments))



---

### Day 29 (Monday, June 22): Spark UI Diagnostics & Review

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)) (Medium) with $O(1)$ operations using two parallel stacks.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Spark UI metrics review.
* **Action**: Run your Project 1 streaming application locally. Open the Spark UI, inspect the **Streaming** tab, and monitor the input rate, processing time, and scheduling delay to ensure your pipeline is healthy.




* **Day 29 Curated Resources**:
*([https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c](https://medium.com/@agrimk16/pyspark-performance-tuning-practical-lessons-for-data-engineers-602a402b614c))
*([https://community.databricks.com/t5/community-articles/9-powerful-spark-optimization-techniques-in-databricks-with-real/td-p/132925](https://community.databricks.com/t5/community-articles/9-powerful-spark-optimization-techniques-in-databricks-with-real/td-p/132925))

---

### Day 30 (Tuesday, June 23): End of Month 1 Portfolio Review & Assessment

* **Time Allocation**: 2.5 Hours
* **Algorithmic Focus (45 Mins)**:
* Solve([https://leetcode.com/problems/evaluate-reverse-polish-notation/](https://leetcode.com/problems/evaluate-reverse-polish-notation/)) (Medium) using stack-based processing.


* **Systems Engineering (1 Hour 45 Mins)**:
* **Concept**: Complete verification of Month 1 milestones.


* **Action**: Verify that your Project 1 PySpark repository is fully functional, cleanly formatted (adhering to PEP8), and contains no hardcoded file paths. Verify that your `README.md` is updated with your local profiling logs, highlighting exactly how you diagnosed and optimized the pipeline.




* **Day 30 Curated Resources**:
*([https://github.com/jrlasak/awesome-databricks](https://github.com/jrlasak/awesome-databricks))
*([https://medium.com/itversity/data-engineering-system-design-6764e0a72e3d](https://medium.com/itversity/data-engineering-system-design-6764e0a72e3d)) 



---

## Actionable Tips to Maximize Month 1 Results

1. **Keep Coding Simple**: Do not try to run heavy pipelines on massive production datasets early on. Focus first on writing clean, reproducible PySpark transformations on the Databricks Free Edition.
2. **Read the Plans Regularly**: Make it a habit to run `.explain(True)` on your PySpark DataFrames. This builds the structural query intuition you will need to ace live system design and optimization rounds.
3. **Analyze Every Failure**: When a Spark job fails, don't just change configurations randomly. Open the Spark UI, identify the exact task that failed, locate the thread dump, and debug with a structured diagnostic mindset.
