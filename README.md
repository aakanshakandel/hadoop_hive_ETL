# hadoop_hive_ETL


## Project Overview

This project involved developing a three-phase ETL (Extract, Transform, Load) pipeline to automate the processing, transformation and analysis of transaction data using Bash scripting, Python, Hadoop, HDFS, MapReduce and Apache Hive.

The objective was to build an automated workflow that could process raw CSV files, clean and standardise transaction records, perform distributed data processing and generate meaningful summaries using Hive SQL.

## Phase 1 – Data Extraction and Transformation (Bash ETL)

The first phase focused on preparing raw transaction data for further processing.

I developed a Bash-based ETL pipeline using AWK to automate the following tasks:

- Extract raw transaction CSV files from a source directory.
- Move files into a staging area for processing.
- Clean the data by removing headers, filtering invalid records and standardising transaction categories.
- Convert transaction values from USD to EUR using a configurable exchange rate.
- Generate transformed CSV files containing three fields: transaction category, place and value in EUR.
- Archive processed source files and generate timestamped logs to track each execution.

The pipeline was designed to support repeatable execution while preventing previously processed files from being duplicated.

## Phase 2 – Hadoop and MapReduce Processing

The second phase extended the ETL pipeline by integrating Hadoop for distributed data processing.

I developed a Bash orchestration script that connected the first phase with Hadoop and automated the following steps:

- Execute the Phase 1 ETL process to prepare transformed data.
- Upload the transformed CSV files into the Hadoop Distributed File System (HDFS).
- Execute a Hadoop Streaming MapReduce job using Python mapper and reducer scripts.
- Process transaction records to calculate the number of transactions in each category.
- Consolidate Hadoop output files into a single timestamped report.
- Clean temporary processing outputs and archive processed files to prevent duplicate processing during subsequent executions.

This phase demonstrated how Hadoop, HDFS and MapReduce could be integrated into an automated data processing workflow.

## Phase 3 – Data Analysis Using Apache Hive

The final phase focused on using Apache Hive to organise and analyse the processed transaction data.

I used Hive SQL to:

- Create a managed Hive table called `phase3_transactions` to store transaction data.
- Load the latest prepared transaction batch from HDFS into the table using overwrite loading.
- Execute SQL queries to calculate transaction counts by category.
- Calculate the total number of transactions and average transaction value across categories.
- Generate aggregated results to support analysis of transaction patterns.

This phase demonstrated how Hive provides a SQL-based interface for analysing data stored in Hadoop.

## Key Learnings

Through this project, I gained practical experience developing an end-to-end ETL pipeline, automating data processing using Bash, working with HDFS, implementing MapReduce using Python and performing analytical queries using Hive.

I also strengthened my troubleshooting skills by identifying and resolving issues involving duplicate processing and HDFS staging files, improving the reliability and repeatability of the pipeline.

**Technologies Used:** Bash, AWK, Python, Hadoop, HDFS, Hadoop Streaming, MapReduce, Apache Hive, HiveQL, Linux.
A video demonstration will be uploaded soon for this. 
