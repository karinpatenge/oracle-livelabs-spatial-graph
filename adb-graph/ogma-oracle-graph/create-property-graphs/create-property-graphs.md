# Create the SQL Property Graphs

## Introduction

In this lab, you create SQL property graphs on top of the dataset tables and run your first graph queries. A SQL property graph only stores metadata that maps tables to vertices and edges, so creating one is fast and the graph always reflects the current table data.

Estimated Time: 20 minutes

### Objectives

In this lab, you will:

* Create a SQL property graph with `CREATE PROPERTY GRAPH`
* Create a second SQL property graph for a different view of the data
* Verify the graphs in the data dictionary
* Query the graphs with `GRAPH_TABLE`

### Prerequisites

This lab assumes you have:

* A SQLcl session connected to the workshop user
* Familiarity with the dataset tables from Lab 3

## Task 1: Create the First Property Graph

1. Create a property graph that maps the entity tables to vertices and the relationship table to edges.

    ```
    <copy>CREATE PROPERTY GRAPH <graph_name_1>
      VERTEX TABLES (
        <vertex_table_1>
          KEY (<id_column>)
          LABEL <vertex_label_1>
          PROPERTIES (<column_1>, <column_2>)
      )
      EDGE TABLES (
        <edge_table_1>
          KEY (<edge_id_column>)
          SOURCE KEY (<source_column>) REFERENCES <vertex_table_1> (<id_column>)
          DESTINATION KEY (<destination_column>) REFERENCES <vertex_table_1> (<id_column>)
          LABEL <edge_label_1>
          PROPERTIES (<column_3>)
      );</copy>
    ```

    *TODO: Replace the placeholders with the final DDL. Optionally provide the script as `files/create-graphs.sql`.*

## Task 2: Create the Second Property Graph

1. Create a second property graph that covers a different subset or perspective of the data.

    ```
    <copy>CREATE PROPERTY GRAPH <graph_name_2>
      VERTEX TABLES (
        <vertex_table_1> KEY (<id_column>) LABEL <vertex_label_1>,
        <vertex_table_2> KEY (<id_column>) LABEL <vertex_label_2>
      )
      EDGE TABLES (
        <edge_table_2>
          KEY (<edge_id_column>)
          SOURCE KEY (<source_column>) REFERENCES <vertex_table_1> (<id_column>)
          DESTINATION KEY (<destination_column>) REFERENCES <vertex_table_2> (<id_column>)
          LABEL <edge_label_2>
      );</copy>
    ```

    *TODO: Define the second graph and explain why it is modeled separately.*

## Task 3: Verify the Graphs

1. List the property graphs in your schema.

    ```
    <copy>SELECT graph_name FROM user_property_graphs;</copy>
    ```

    Both graphs appear in the result.

## Task 4: Query the Graphs

1. Find vertices connected by an edge. `GRAPH_TABLE` returns the matched pattern as rows, so you can combine it with any SQL.

    ```
    <copy>SELECT *
    FROM GRAPH_TABLE ( <graph_name_1>
           MATCH (a IS <vertex_label_1>) -[e IS <edge_label_1>]-> (b IS <vertex_label_1>)
           COLUMNS (a.<id_column> AS source_id,
                    b.<id_column> AS target_id)
         )
    FETCH FIRST 10 ROWS ONLY;</copy>
    ```

2. Follow paths of variable length, for example one to three hops from a given vertex.

    ```
    <copy>SELECT *
    FROM GRAPH_TABLE ( <graph_name_1>
           MATCH (a IS <vertex_label_1>) -[e IS <edge_label_1>]->{1,3} (b IS <vertex_label_1>)
           WHERE a.<id_column> = <start_id>
           COLUMNS (a.<id_column> AS source_id,
                    b.<id_column> AS target_id)
         );</copy>
    ```

    *TODO: Add the queries that the Ogma application uses in Lab 5, with expected results.*

You may now **proceed to the next lab**.

## Learn More

* [SQL Property Graphs in the Oracle Database Graph Developer's Guide](https://docs.oracle.com/en/database/oracle/property-graph/)
* [CREATE PROPERTY GRAPH in the SQL Language Reference](https://docs.oracle.com/en/database/oracle/oracle-database/)

## Acknowledgements

* **Author** - Karin Patenge, Oracle Database Product Management, Spatial and Graph
* **Contributors** - *TODO*
* **Last Updated By/Date** - Karin Patenge, October 2026
