# Introduction

## About This Workshop

Connected data hides patterns that rows and columns do not show: which account logs on to which computer, or how far an intruder spreads through a network. In this workshop, you model relational tables as SQL property graphs in Oracle Autonomous AI Database. You query the graphs with SQL/PGQ, analyze them in Graph Studio, and explore them visually with Linkurious Ogma.

You work in a LiveLabs Sandbox. LiveLabs prepares it with the database, the dataset, and JupyterLab already installed. You spend your time on graphs, not on setup.

Estimated Workshop Time: 1 hour

### Watch the Video

The video shows where the workshop leads: an Ogma visualization of the stolen credentials in the LANL data. Ogma groups the victim computers by the attacker identity that reached them. It switches between a force and a hierarchical layout and replays the logons on a timeline. The video has no sound.

[Ogma visualization of the stolen credentials in the LANL data](video:../../introduction/images/ogma-demo-stolen-credentials.mp4:medium)

### Objectives

In this workshop, you will:

- Learn how intruders hide in regular network activity.
- Connect to an Oracle Autonomous AI Database and explore the LANL cyber-security dataset.
- Create property graphs from the security event records.
- Analyze the graphs with notebooks in Graph Studio.
- Visualize and explore the graphs with Linkurious Ogma in JupyterLab.

### About SQL Property Graphs

A SQL property graph is a schema object that maps existing tables to vertices and edges. It stores only metadata, not data. Graph queries therefore always see current table data and use the same security, transactions, and indexes as the tables. You query a SQL property graph with the `GRAPH_TABLE` operator from the SQL:2023 standard (SQL/PGQ).

### About Linkurious Ogma

Ogma is a JavaScript library from Linkurious for interactive graph visualization. It renders large graphs in the browser and provides APIs for layouts, styling, and interaction. In this workshop, you use Ogma from notebooks in JupyterLab.

### What Is Already Set Up for You

Your LiveLabs sandbox reservation prepares the environment before you start:

- An Oracle Autonomous AI Database 26ai.
- The database user `GRAPHUSER` with the LANL tables loaded.
- A JupyterLab environment.

### Prerequisites

This workshop assumes you have:

- A LiveLabs sandbox reservation for this workshop.
- Basic SQL skills.
- Optional: basic familiarity with JavaScript, to follow the Ogma code.

## Learn More

- [Oracle Database Graph Developer's Guide for Property Graph](https://docs.oracle.com/en/database/oracle/property-graph/)
- [Oracle Graph product page](https://www.oracle.com/database/graph/)
- [LANL Comprehensive, Multi-Source Cyber-Security Events dataset](https://csr.lanl.gov/data/cyber1/)
- [Ogma integration with Oracle](https://doc.linkurious.com/ogma/5.3/tutorials/oracle)
- [Linkurious Ogma documentation](https://doc.linkurious.com/ogma/latest/)

## Acknowledgements

* **Author** - Karin Patenge, Database Product Management
* **Contributors** - Hans Viehmann, Léo Nicolle (Linkurious), Ramu Murakami Gutierrez
* **Last Updated By/Date** - Karin Patenge, December 2026
