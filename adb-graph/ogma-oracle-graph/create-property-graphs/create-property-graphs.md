# Create the Cyber Threat Graphs

## Introduction

In this lab, you create two SQL property graphs on top of the LANL tables. Your sandbox already contains the five event tables and the three entity tables that the graphs use.

- The **ground-truth graph** holds only the known compromise events from the authorized security exercise. It tells you what the intruders actually did.
- The **cyber graph** connects the authentication, DNS, network flow, and process events. It shows all activity on the network, regular and malicious.

A property graph does not copy any data. It defines how table rows form vertices and edges. You can then query the tables as a graph.

Estimated Time: 10 minutes

### Objectives

In this lab, you will:

- Open a SQL worksheet as `GRAPHUSER`.
- Create the ground-truth graph `LANL_GROUND_TRUTH_GRAPH`.
- Create the cyber graph `LANL_CYBER_GRAPH`.
- Check that both graphs exist and return data.

> **Note:** Run the blocks one at a time. Paste a block into an empty worksheet and click **Run Script**. Check the result before you run the next block.

## Task 1: Open a SQL Worksheet

1. On your reservation page, click **View Login Info**. Copy the **SQL Worksheet URL**, the database user `GRAPHUSER`, and its password.

2. Open the SQL Worksheet URL in a new browser tab and sign in as `GRAPHUSER`.

3. Run this query with **Run Script**. It lists the tables that the graphs use.

    ```sql
    <copy>
    -- -------------LAB 1 TASK 1 STEP 3-------------
    SELECT table_name, num_rows
    FROM user_tables
    WHERE table_name IN ('AUTH', 'DNS', 'FLOWS', 'PROC', 'REDTEAM',
                         'COMPUTER', 'USER_DOMAIN', 'PROCESS')
    ORDER BY table_name;
    </copy>
    ```

    The query returns eight rows. `NUM_ROWS` shows the row count from the last statistics run.

## Task 2: Create Cyber Threat Property Graphs

Both graphs share the same three vertex tables:

| Vertex label | Table | Represents |
| --- | --- | --- |
| `user_domain` | `USER_DOMAIN` | An account, written as user@domain |
| `computer` | `COMPUTER` | A desktop, server, or other host |
| `process` | `PROCESS` | A program that runs on a computer |

The edges come from the event tables. One event table can feed more than one edge table. For example, one `AUTH` row produces three edges. The first links the source account to the source computer. The second links the destination account to the destination computer. The third links the two computers.

1. Prepare the session and remove any graphs from an earlier run. Paste the block and click **Run Script**.

    ```sql
    <copy>
    -- -------------LAB 1 TASK 2 STEP 1-------------
    ALTER SESSION FORCE PARALLEL QUERY;
    ALTER SESSION ENABLE PARALLEL DDL;
    ALTER SESSION ENABLE PARALLEL DML;

    DROP PROPERTY GRAPH IF EXISTS lanl_ground_truth_graph;
    DROP PROPERTY GRAPH IF EXISTS lanl_cyber_graph;
    </copy>
    ```

2. Create the ground-truth graph from the `REDTEAM` table. Paste the block and click **Run Script**.

    ```sql
    <copy>
    -- -------------LAB 1 TASK 2 STEP 2-------------
    CREATE PROPERTY GRAPH IF NOT EXISTS lanl_ground_truth_graph
      VERTEX TABLES (
        user_domain
          KEY ( user_domain )
          LABEL user_domain PROPERTIES ARE ALL COLUMNS,
        computer
          KEY ( computer )
          LABEL computer PROPERTIES ARE ALL COLUMNS,
        process AS process
          KEY ( process )
          LABEL process PROPERTIES ARE ALL COLUMNS
      )
      EDGE TABLES (
        redteam AS redteam_user_authenticated_computer
          KEY ( id )
          SOURCE KEY ( user_domain ) REFERENCES user_domain ( user_domain )
          DESTINATION KEY ( src_computer ) REFERENCES computer ( computer )
          LABEL authenticated PROPERTIES ( id, time, user_domain, src_computer ),
        redteam AS redteam_computer_compromised_computer
          KEY ( id )
          SOURCE KEY ( src_computer ) REFERENCES computer ( computer )
          DESTINATION KEY ( dst_computer ) REFERENCES computer ( computer )
          LABEL compromised PROPERTIES ( id, time, user_domain, src_computer, dst_computer )
      );
    </copy>
    ```

    Each `REDTEAM` row becomes two edges. An `authenticated` edge links the compromised account to the computer it started from. A `compromised` edge links that computer to the computer the intruder reached.

3. Create the cyber graph from the `AUTH`, `DNS`, `FLOWS`, and `PROC` tables. Paste the block and click **Run Script**.

    ```sql
    <copy>
    -- -------------LAB 1 TASK 2 STEP 3-------------
    CREATE PROPERTY GRAPH IF NOT EXISTS lanl_cyber_graph
      VERTEX TABLES (
        user_domain
          KEY ( user_domain )
          LABEL user_domain PROPERTIES ARE ALL COLUMNS,
        computer
          KEY ( computer )
          LABEL computer PROPERTIES ARE ALL COLUMNS,
        process AS process
          KEY ( process )
          LABEL process PROPERTIES ARE ALL COLUMNS
      )
      EDGE TABLES (
        dns AS dns_computer_resolved_computer
          KEY ( id )
          SOURCE KEY ( src_computer ) REFERENCES computer ( computer )
          DESTINATION KEY ( computer_resolved ) REFERENCES computer ( computer )
          LABEL resolved PROPERTIES ( id, time, src_computer, computer_resolved ),
        flows AS flows_computer_connected_computer
          KEY ( id )
          SOURCE KEY ( src_computer ) REFERENCES computer ( computer )
          DESTINATION KEY ( dst_computer ) REFERENCES computer ( computer )
          LABEL flows_connected PROPERTIES ( id, time, duration, src_computer, src_port, dst_port, dst_computer, protocol, packet_cnt, byte_cnt ),
        proc AS proc_user_authenticated_computer
          KEY ( id )
          SOURCE KEY ( user_domain ) REFERENCES user_domain ( user_domain )
          DESTINATION KEY ( computer ) REFERENCES computer ( computer )
          LABEL proc_connected PROPERTIES ( id, time, user_domain, computer ),
        proc AS proc_computer_runs_process
          KEY ( id )
          SOURCE KEY ( computer ) REFERENCES computer ( computer )
          DESTINATION KEY ( process_name ) REFERENCES process ( process )
          LABEL ran PROPERTIES ( id, time, computer, process_name, start_end ),
        auth AS auth_src_user_authenticated_src_computer
          KEY ( id )
          SOURCE KEY ( src_user_domain ) REFERENCES user_domain ( user_domain )
          DESTINATION KEY ( src_computer ) REFERENCES computer ( computer )
          LABEL auth_src_authenticated PROPERTIES (id, time, src_user_domain, src_computer, auth_type, logon_type, auth_orientation, success_failure, redteam ),
        auth AS auth_dst_user_authenticated_dst_computer
          KEY ( id )
          SOURCE KEY ( dst_user_domain ) REFERENCES user_domain ( user_domain )
          DESTINATION KEY ( dst_computer ) REFERENCES computer ( computer )
          LABEL auth_dst_authenticated PROPERTIES (id, time, dst_user_domain, dst_computer, auth_type, logon_type, auth_orientation, success_failure, redteam ),
        auth AS auth_src_computer_connected_dst_computer
          KEY ( id )
          SOURCE KEY ( src_computer ) REFERENCES computer ( computer )
          DESTINATION KEY ( dst_computer ) REFERENCES computer ( computer )
          LABEL auth_connected PROPERTIES (id, time, src_computer, dst_computer, redteam )
      );
    </copy>
    ```

    The cyber graph has seven edge labels:

    | Edge label | Source table | From | To |
    | --- | --- | --- | --- |
    | `resolved` | `DNS` | Computer that asks | Computer it resolves |
    | `flows_connected` | `FLOWS` | Source computer | Destination computer |
    | `proc_connected` | `PROC` | Account | Computer that runs the process |
    | `ran` | `PROC` | Computer | Process that starts or stops |
    | `auth_src_authenticated` | `AUTH` | Source account | Source computer |
    | `auth_dst_authenticated` | `AUTH` | Destination account | Destination computer |
    | `auth_connected` | `AUTH` | Source computer | Destination computer |

    The `AUTH` edges keep the `redteam` property. It marks the authentication events that belong to the security exercise.

4. Check that both graphs exist. Paste the query and click **Run Script**.

    ```sql
    <copy>
    -- -------------LAB 1 TASK 2 STEP 4-------------
    SELECT graph_name
    FROM user_property_graphs
    ORDER BY graph_name;
    </copy>
    ```

    The query returns `LANL_CYBER_GRAPH` and `LANL_GROUND_TRUTH_GRAPH`.

5. Query the ground-truth graph. This query counts the `compromised` edges, one for each compromise event.

    ```sql
    <copy>
    -- -------------LAB 1 TASK 2 STEP 5-------------
    SELECT COUNT(*) AS compromise_events
    FROM GRAPH_TABLE ( lanl_ground_truth_graph
      MATCH (s IS computer) -[e IS compromised]-> (d IS computer)
      COLUMNS ( e.id AS id )
    );
    </copy>
    ```

    The count matches the number of rows in the `REDTEAM` table.

You can also download the complete script: [create-graphs.sql](files/create-graphs.sql).

## Learn More

- [LANL Comprehensive, Multi-Source Cyber-Security Events dataset](https://csr.lanl.gov/data/cyber1/)

## Acknowledgements

* **Author** - Karin Patenge, Database Product Management
* **Contributors** - Hans Viehmann, Léo Nicolle (Linkurious), Ramu Murakami Gutierrez
* **Last Updated By/Date** - Karin Patenge, December 2026
