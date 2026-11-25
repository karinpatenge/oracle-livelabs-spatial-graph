# Provision the Sandbox Environment

## Introduction

In this lab, you reserve a LiveLabs Sandbox for this workshop. LiveLabs provisions the environment in an Oracle-owned tenancy from an Oracle Cloud Marketplace image, so you do not need your own Oracle Cloud account or any manual installation.

Estimated Time: 10 minutes

### About the Sandbox Environment

The Marketplace image deploys a compute instance that already contains everything the workshop needs. *TODO: Confirm the components below against the final Marketplace image.*

| Component | Purpose |
| --- | --- |
| Oracle Database *TODO: version* | Stores the dataset and the SQL property graphs |
| Sample dataset | Relational tables used to build the graphs |
| SQLcl / SQL Developer *TODO: confirm* | Run SQL statements against the database |
| Node.js runtime *TODO: confirm* | Runs the Ogma visualization application |
| Ogma web application | Visualizes graph query results in the browser |
| noVNC remote desktop | Browser-based access to the instance desktop |

### Objectives

In this lab, you will:

* Request a LiveLabs Sandbox reservation for this workshop
* Track the reservation until the environment is ready
* Understand which resources the Marketplace image provisions

### Prerequisites

This lab assumes you have:

* An Oracle account to sign in to LiveLabs

## Task 1: Request a Sandbox Reservation

1. Open the workshop page in LiveLabs. *TODO: Add the public workshop URL after publication.*

2. Click **Start**, and then select **Run on LiveLabs Sandbox**.

    *TODO: Add a screenshot, for example `images/start-sandbox.png`.*

3. Sign in with your Oracle account if prompted.

4. Choose when the reservation should start. Select **Start Workshop Now** to provision immediately, or pick a later date and time.

5. Review and accept the terms, and then click **Submit Reservation**.

    > **Note:** The reservation runs for a fixed duration. You can extend it later from **My Reservations** if your time runs short.

## Task 2: Wait for the Environment to Be Provisioned

1. LiveLabs sends an email when it receives your reservation and another when the environment is ready. Provisioning usually takes *TODO: minutes*.

2. To check the status, click your profile icon in LiveLabs and select **My Reservations**. The status changes from *Provisioning* to *Available* when the environment is ready.

    *TODO: Add a screenshot, for example `images/my-reservations.png`.*

3. When the status is *Available*, click **Launch Workshop** to open the workshop instructions with your reservation details.

## Task 3: Review the Provisioned Resources

1. In the workshop instructions, click **View Login Info**. The reservation page lists the resources created for you. *TODO: Confirm the exact fields shown for this workshop.*

    * Remote desktop URL
    * Public IP address of the compute instance
    * Database user name and password
    * Ogma application URL

2. Keep this page open. You need these values in the next lab.

You may now **proceed to the next lab**.

## Learn More

* [LiveLabs FAQ](https://livelabs.oracle.com/pls/apex/f?p=133:100:::::SEARCH:faq)
* [Oracle Cloud Marketplace](https://cloudmarketplace.oracle.com/)

## Acknowledgements

* **Author** - Karin Patenge, Oracle Database Product Management, Spatial and Graph
* **Contributors** - *TODO*
* **Last Updated By/Date** - Karin Patenge, October 2026
