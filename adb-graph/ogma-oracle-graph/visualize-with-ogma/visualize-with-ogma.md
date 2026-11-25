# Visualize the SQL Property Graphs with Linkurious Ogma

## Introduction

In this lab, you explore the SQL property graphs in a browser. A web application on the Sandbox runs `GRAPH_TABLE` queries against Oracle Database, converts the results to nodes and edges, and renders them with Linkurious Ogma. You load a graph, change layouts and styles, expand neighborhoods, and run your own query.

Estimated Time: 25 minutes

### About the Application

*TODO: Describe the application architecture in two or three sentences, for example: browser with Ogma, a Node.js backend that connects to the database with node-oracledb, and a REST endpoint that returns graph JSON. Add a diagram, for example `images/architecture.png`.*

### Objectives

In this lab, you will:

* Load a SQL property graph into the Ogma application
* Apply layouts and styles to make patterns visible
* Expand the neighborhood of a selected vertex
* Visualize the result of a custom `GRAPH_TABLE` query

### Prerequisites

This lab assumes you have:

* The SQL property graphs created in Lab 4
* The Ogma application open in the remote desktop browser

## Task 1: Load a Graph

1. In the remote desktop browser, open the Ogma application.

    ```
    <copy>http://localhost:<port></copy>
    ```

2. Select `<graph_name_1>` and load it. The application queries the graph and draws the vertices and edges.

    *TODO: Describe the exact UI controls and add a screenshot, for example `images/load-graph.png`.*

## Task 2: Change the Layout and Style

1. Apply a force-directed layout to spread out the graph and reveal clusters.

2. Color or size vertices by a property, for example by label or by degree.

    *TODO: List the layouts and style options the application exposes. If learners edit code, show the relevant Ogma snippet, for example a call to `ogma.layouts.force()`.*

## Task 3: Expand a Neighborhood

1. Select a vertex and expand it to load its direct neighbors from the database.

2. Expand one of the neighbors to follow the path one hop further.

    *TODO: Explain which `GRAPH_TABLE` query the application runs on expand.*

## Task 4: Visualize a Custom Query

1. Enter a `GRAPH_TABLE` query in the application, for example the variable-length path query from Lab 4.

    ```
    <copy>SELECT *
    FROM GRAPH_TABLE ( <graph_name_1>
           MATCH (a IS <vertex_label_1>) -[e IS <edge_label_1>]->{1,3} (b IS <vertex_label_1>)
           WHERE a.<id_column> = <start_id>
           COLUMNS (vertex_id(a) AS a_id, edge_id(e) AS e_id, vertex_id(b) AS b_id)
         );</copy>
    ```

2. Run the query and review the resulting subgraph.

3. Repeat with `<graph_name_2>` and compare the two perspectives on the data.

    *TODO: Confirm the column contract the application expects from custom queries.*

You may now **proceed to the next lab**.

## Learn More

* [Linkurious Ogma documentation](https://doc.linkurious.com/ogma/latest/)
* [node-oracledb documentation](https://node-oracledb.readthedocs.io/)

## Acknowledgements

* **Author** - Karin Patenge, Oracle Database Product Management, Spatial and Graph
* **Contributors** - *TODO*
* **Last Updated By/Date** - Karin Patenge, October 2026
