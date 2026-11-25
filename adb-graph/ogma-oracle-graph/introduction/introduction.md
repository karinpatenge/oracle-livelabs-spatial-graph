# Introduction

## About this Workshop

Connected data hides patterns that rows and columns do not show: who transacts with whom, or how far a risk spreads through a network. In this workshop, you model relational tables as SQL property graphs in Oracle Database. You query the graphs with SQL/PGQ and explore the results in a web application built with Linkurious Ogma.

You work in a LiveLabs Sandbox. LiveLabs builds it from an Oracle Cloud Marketplace image with the database, the dataset, and the visualization application already installed. You spend your time on graphs, not on setup.

*TODO: Replace the use-case sentence above with the business scenario of the final dataset.*

Estimated Workshop Time: 1 hour 45 minutes

*TODO: Confirm the total time after the placeholder labs are defined. Optionally add a video with `[](youtube:VIDEO_ID)`.*

### About SQL Property Graphs

A SQL property graph is a schema object that maps existing tables to vertices and edges. It stores only metadata, not data. Graph queries therefore always see current table data and use the same security, transactions, and indexes as the tables. You query a SQL property graph with the `GRAPH_TABLE` operator from the SQL:2023 standard (SQL/PGQ).

### About Linkurious Ogma

Ogma is a JavaScript library from Linkurious for interactive graph visualization in web applications. It renders large graphs in the browser and provides APIs for layouts, styling, and interaction. In this workshop, a small web application queries Oracle Database and hands the results to Ogma.

### Objectives

In this workshop, you will:

* Provision and connect to a LiveLabs Sandbox built from an Oracle Cloud Marketplace image
* Explore the tables that make up the sample dataset
* Create SQL property graphs on top of those tables
* Query the graphs with `GRAPH_TABLE`
* Visualize and explore the graphs with Linkurious Ogma

*TODO: Add objectives for Lab 6 and Lab 7 once their scope is defined.*

### Prerequisites

This workshop assumes you have:

* An Oracle account to sign in to LiveLabs
* Basic familiarity with SQL
* Optional: basic familiarity with JavaScript, to follow the Ogma application code

This workshop was last tested with *TODO: Marketplace image name and version, Oracle Database version, Ogma version*.

## Learn More

* [Oracle Database Graph Developer's Guide for Property Graph](https://docs.oracle.com/en/database/oracle/property-graph/)
* [Oracle Graph product page](https://www.oracle.com/database/graph/)
* [Linkurious Ogma documentation](https://doc.linkurious.com/ogma/latest/)

## Acknowledgements

* **Author** - Karin Patenge, Oracle Database Product Management, Spatial and Graph
* **Contributors** - *TODO*
* **Last Updated By/Date** - Karin Patenge, October 2026
