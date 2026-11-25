# Workshop Details

Reusable text for the LiveLabs Workshop Management System (WMS). Keep it aligned with `workshops/sandbox/manifest.json`.

* **WMS ID** - 12172
* **Branch** - `WMS_ID_12172`
* **Workshop folder** - `adb-graph/ogma-oracle-graph`
* **Environment** - LiveLabs Sandbox only, provisioned from an Oracle Cloud Marketplace image
* **Help alias** - livelabs-help-sg_us@oracle.com

## Title

Build and Visualize SQL Property Graphs with Oracle Database and Linkurious Ogma

## Short Description

Model relational tables as SQL property graphs in Oracle Database, query them with SQL/PGQ, and explore the results interactively with Linkurious Ogma in a ready-to-use LiveLabs Sandbox.

## Long Description

Relationships in your data, such as who transacts with whom or how entities connect across systems, are often buried in foreign keys and join tables. SQL property graphs in Oracle Database let you work with these relationships directly: you define vertices and edges on top of existing tables, without copying data, and query patterns and paths with the `GRAPH_TABLE` operator from the SQL:2023 standard.

In this workshop, you use a LiveLabs Sandbox provisioned from an Oracle Cloud Marketplace image that already contains the database, a sample dataset, and a visualization application. You explore the dataset, create SQL property graphs, run graph queries, and visualize the results in a web application built with Linkurious Ogma, a JavaScript library for interactive graph visualization.

*TODO: Add one sentence about the scenario of the final dataset and the topics of Lab 6 and Lab 7.*

## Workshop Outline

1. Introduction
2. Lab 1: Provision the Sandbox Environment
3. Lab 2: Connect to the Sandbox Environment
4. Lab 3: Explore the Dataset
5. Lab 4: Create the SQL Property Graphs
6. Lab 5: Visualize the SQL Property Graphs with Linkurious Ogma
7. Lab 6: Lab Placeholder 1
8. Lab 7: Lab Placeholder 2

## Workshop Prerequisites

* An Oracle account to sign in to LiveLabs
* Basic familiarity with SQL
* Optional: basic familiarity with JavaScript

## Estimated Time

1 hour 45 minutes (Lab 1: 10 min, Lab 2: 10 min, Lab 3: 10 min, Lab 4: 20 min, Lab 5: 25 min, Lab 6: 15 min, Lab 7: 15 min). *TODO: Confirm after testing.*

## Open Items Before Publication

* Marketplace image: name, version, listing URL, and the components it installs (database version, service name, users, Node.js, Ogma application, ports).
* Reservation details: provisioning time, reservation duration, and the fields shown under **View Login Info**.
* Dataset: name, domain, origin, license, table names, and a data model diagram.
* Final `CREATE PROPERTY GRAPH` statements and queries; consider shipping them in `create-property-graphs/files/`.
* Ogma application: architecture, UI controls, start-up procedure, and Ogma license terms for the Sandbox.
* Scope and titles of Lab 6 and Lab 7; rename their folders and manifest entries.
* Screenshots for every `TODO: Add a screenshot` note, saved as lowercase, dash-separated PNG files in each lab's `images/` folder.
* Remove all `TODO` notes.
