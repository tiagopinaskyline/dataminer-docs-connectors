---
uid: Connector_help_VOO_CMTS_Collector
---

# VOO CMTS Collector

The **VOO CMTS Collector** is a combination of a smart-serial connector, SNMPv2 and serial connector.

## About

This connector is used to collect data from the CMTS devices at VOO. This data is polled by using SNMP and IPDR commands and is sent to the relevant **CPE Manager** and **MTA Collector.** In other words, the connector is used as a control center to parse and distribute information from approximately 60 000 **CPEs**.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

This connector uses a Simple Network Management Protocol (SNMP) and a smart-serial connection and requires the following input during element creation:

**SNMP CONNECTION**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*
- **Device address**: Not needed.

**SNMP Settings**:

- **Port number**: The port of the connected device, by default *161.*
- **Get community string**: The community string in order to read from the device. The default value is *CADMIUM*.
- **Set community string**: The community string in order to set to the device. The default value is *private.*

**SERIAL CONNECTION**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13.*
- **IP port**: The port of the connected device. By default, this is *4737*.
- **Bus address**: The **Collector Name** should be filled in here. By default, this is *DMA-COL-01*.

**SSH CONNECTION**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13.*
- **IP port**: Default is 22.

## Usage

### General

This page contains general information related to the device. In addition, you can extract a **Debug File** with all the **MAC addresses and Channels** for each **CPE**. The **IPDR Templates and Sessions** are also displayed and can be requested.

Another important parameter on this page is **IPDR Data Timeout.** This parameter defines after how much time the connection is considered to be lost. The value of **Seconds Since Last Data** is compared with this value. 

### Offload
This page contains the **Offload Status Table**, used to monitor the status of files for offloading. It also includes the following parameters:

**Offload State**: Enable or disable the offload mechanism.
**Force Offload**: Forces all files displayed in the table to offload, regardless of their content.
**Offload Status**: Displays the overall offloading status, calculated based on the **Status** values from the **Offload Status Table**:

  - **N/A**: All table rows display **N/A**.
  - **OK**: All table rows are either **N/A** or **OK**, with at least one **OK**.
  - **Partial**: There is at least one offload file showing the **Partial** status (Priority 2).
  - **Failure**: There is at least one offload file showing the **Fail** status (Priority 1).

**Offload Status Table**: 
  - **State**: The user can enable or disable the offloading process, and also force its execution.
  - **Status**:
    - **N/A**: No data available for offloading.
    - **OK**: File successfully offloaded.
    - **Partial**: At least one column value in the table is not filled in.
    - **Failure**: The offloading process encountered an error (e.g., an exception).
    - **Missing Entries**: Indicates the number of table rows that are not completely filled in.
    - **Force Button**: Offloads the file regardless of the file's content.

### Logging

This page contains the **Logging Table**, which consists of all **IPDR Administrator Error/Log Messages.**
