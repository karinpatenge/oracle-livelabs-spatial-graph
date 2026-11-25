# Connect to the Sandbox Environment

## Introduction

In this lab, you open the remote desktop of your Sandbox instance, connect to Oracle Database as the workshop user, and confirm that the Ogma application is reachable.

Estimated Time: 10 minutes

### Objectives

In this lab, you will:

* Open the noVNC remote desktop of the Sandbox instance
* Connect to the database with SQLcl
* Confirm that the Ogma application is running

### Prerequisites

This lab assumes you have:

* An available LiveLabs Sandbox reservation for this workshop

## Task 1: Open the Remote Desktop

1. In the workshop instructions, click **View Login Info**.

2. Copy the **Remote Desktop** URL and open it in a new browser tab. The desktop of the compute instance opens in your browser.

    *TODO: Add a screenshot, for example `images/novnc-desktop.png`.*

3. Optional: To copy text from your computer into the remote desktop, open the noVNC control bar on the left edge of the screen and use the **Clipboard** panel.

## Task 2: Connect to the Database

1. On the remote desktop, open a terminal window.

2. Start SQLcl and connect as the workshop user. Replace the placeholders with the values from **View Login Info**.

    ```
    <copy>sql <db_user>/<db_password>@localhost:1521/<service_name></copy>
    ```

    *TODO: Replace the placeholders with the actual user, connect string, and service name from the Marketplace image.*

3. Verify the connection.

    ```
    <copy>SELECT user, sys_context('USERENV', 'CON_NAME') AS pdb FROM dual;</copy>
    ```

    The query returns the workshop user and the pluggable database name.

## Task 3: Check the Ogma Application

1. On the remote desktop, open the browser and go to the Ogma application URL.

    ```
    <copy>http://localhost:<port></copy>
    ```

    *TODO: Replace `<port>` with the port the application listens on, and document how the application is started if it is not started automatically.*

2. Confirm that the application page loads. You use it in Lab 5.

## Task 4: Connect with SSH (Optional)

1. If you prefer a local terminal, connect to the instance with SSH using the public IP address and private key from **View Login Info**.

    ```
    <copy>ssh -i <private_key_file> opc@<public_ip></copy>
    ```

    *TODO: Confirm the OS user name and whether the reservation provides an SSH key.*

You may now **proceed to the next lab**.

## Learn More

* [SQLcl documentation](https://docs.oracle.com/en/database/oracle/sql-developer-command-line/)

## Acknowledgements

* **Author** - Karin Patenge, Oracle Database Product Management, Spatial and Graph
* **Contributors** - *TODO*
* **Last Updated By/Date** - Karin Patenge, October 2026
