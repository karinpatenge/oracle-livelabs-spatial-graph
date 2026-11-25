# Workshop Details

Reusable text for the LiveLabs Workshop Management System (WMS). Keep it aligned with `workshops/sandbox/manifest.json`.

* **WMS ID** - 12172
* **Branch** - `WMS_ID_12172`
* **Workshop folder** - `adb-graph/ogma-oracle-graph`
* **Environment** - LiveLabs Sandbox (green button) with Oracle Autonomous AI Database 26ai and JupyterLab, built from an image that the LiveLabs team provides
* **Sandbox instructions** - `workshops/sandbox/index.html`. Link this page in WMS so that learners see **Preview Sandbox Instructions** when they click **Start**.
* **Help alias** - livelabs-help-db_us@oracle.com (as in the manifest)

## Title

From Security Events to Attack Paths: Graph-powered Cyber Threat Hunting using Oracle Property Graph and Linkurious Ogma

## Short Description

Connect 58 days of real network security events into SQL property graphs in Oracle Autonomous AI Database, analyze them in Graph Studio, and follow an intruder's path with Linkurious Ogma.

## Long Description

An intruder who uses a valid employee account is hard to spot. Every logon succeeds, and each step alone can look legitimate. Only the way the steps connect gives the intruder away.

In this workshop, you investigate real network activity that Los Alamos National Laboratory (LANL) published: authentication, process, network flow, and DNS events, plus known compromise events from an authorized security exercise. You create SQL property graphs on top of the event tables, analyze them with Graph Studio notebooks, and visualize the attack paths with Linkurious Ogma in JupyterLab. Everything runs in a ready-to-use LiveLabs Sandbox.

## Workshop Outline

1. Introduction
2. About the Cyber Threat
3. Exploring the Dataset
4. Lab 1: Create the Cyber Threat Graphs
5. Lab 2: Analyze the Cyber Threat Graphs
6. Lab 3: Visualize the Cyber Threat Graphs
7. Need Help?

## Workshop Prerequisites

* An Oracle account to sign in to LiveLabs
* Basic SQL skills
* Optional: basic familiarity with JavaScript

## Estimated Time

1 hour (About the Cyber Threat: 5 min, Exploring the Dataset: 10 min, Lab 1: 10 min, Lab 2: 20 min, Lab 3: 15 min). Confirm after testing.

## Open Items Before Publication

* Fields shown under **View Login Info** in the sandbox reservation (Database Actions URL, `GRAPHUSER` password, JupyterLab URL).
* Content of Lab 2 (Graph Studio notebooks) and Lab 3 (Ogma notebooks in JupyterLab).
* Screenshots for each lab, saved as lowercase, dash-separated files in each lab's `images/` folder.
* Help alias: confirm `livelabs-help-db_us@oracle.com` or `livelabs-help-sg_us@oracle.com`.
* Ogma license terms for the sandbox.
