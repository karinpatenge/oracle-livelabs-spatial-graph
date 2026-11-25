# Explore the Dataset

## Introduction

In this lab, you look at the tables that ship with the Sandbox and identify which ones hold entities and which ones hold relationships. That distinction decides how the tables map to vertices and edges when you create the SQL property graphs in the next lab.

Estimated Time: 10 minutes

### About the Dataset

*TODO: Describe the dataset in two or three sentences: domain, origin, size, and license. If the data comes from a non-Oracle source, record its owner and the usage approval in `TRACEABILITY.md`.*

| Table | Role in the graph | Description |
| --- | --- | --- |
| `<vertex_table_1>` | Vertex | *TODO* |
| `<vertex_table_2>` | Vertex | *TODO* |
| `<edge_table_1>` | Edge | *TODO* |
| `<edge_table_2>` | Edge | *TODO* |

*TODO: Add a data model diagram, for example `images/data-model.png`.*

### Objectives

In this lab, you will:

* List the tables in the workshop schema
* Review keys and foreign keys that connect the tables
* Inspect sample rows and row counts

### Prerequisites

This lab assumes you have:

* A SQLcl session connected to the workshop user

## Task 1: List the Tables

1. List the tables in the workshop schema.

    ```
    <copy>SELECT table_name, num_rows
    FROM   user_tables
    ORDER  BY table_name;</copy>
    ```

2. Describe each table to see its columns.

    ```
    <copy>DESCRIBE <vertex_table_1></copy>
    ```

## Task 2: Review the Relationships

1. List the primary and foreign keys. Each foreign key is a candidate edge in the graph.

    ```
    <copy>SELECT c.table_name, c.constraint_name, c.constraint_type,
           cc.column_name, r.table_name AS referenced_table
    FROM   user_constraints c
    JOIN   user_cons_columns cc ON cc.constraint_name = c.constraint_name
    LEFT JOIN user_constraints r ON r.constraint_name = c.r_constraint_name
    WHERE  c.constraint_type IN ('P', 'R')
    ORDER  BY c.table_name, c.constraint_type;</copy>
    ```

## Task 3: Inspect Sample Data

1. Look at a few rows from an entity table and a relationship table.

    ```
    <copy>SELECT * FROM <vertex_table_1> FETCH FIRST 5 ROWS ONLY;
    SELECT * FROM <edge_table_1> FETCH FIRST 5 ROWS ONLY;</copy>
    ```

2. Count the rows in each table to get a sense of the graph size.

    ```
    <copy>SELECT COUNT(*) FROM <vertex_table_1>;</copy>
    ```

    *TODO: Replace all `<table>` placeholders with the final table names and add the expected results.*

You may now **proceed to the next lab**.

## Acknowledgements

* **Author** - Karin Patenge, Oracle Database Product Management, Spatial and Graph
* **Contributors** - *TODO*
* **Last Updated By/Date** - Karin Patenge, October 2026
