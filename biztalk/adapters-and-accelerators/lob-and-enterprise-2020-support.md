---
title: Supported Line-of-Business (LOB) and Enterprise systems
description: Details of Line-of-Business (LOB) and Enterprise systems supported by BizTalk Server 2020
ms.date: 01/14/2026
ms.topic: partner-tools
ms.service: biztalk-server
# optional metadata
#ROBOTS:
ms.reviewer: 
ms.suite:
ms.custom: biztalk-2020
---

# Supported Line-of-Business (LOB) and Enterprise systems in BizTalk Server 2020

This article lists the Line-of-Business (LOB) and Enterprise systems supported by **BizTalk Server 2020**, including:

- SAP Server
- SAP client
- Oracle Database
- Oracle client
- Oracle E-Business Suite
- Siebel Server
- Sieble Client
- SQL Server
- JD Edwards Enterprise One
- People Soft Enterprise
- TIBCO Rendezvous
- TIBCO Enterprise Message Service

> [!NOTE]
> This feature applies to BizTalk Server 2020 and newer. The BizTalk Adapter Pack (BAP) is included with the BizTalk Server installation. It doesn't require a separate installation.

## Supported LOB systems

### SAP Server

- SAP ECC 6.0 Unicode
- SAP ECC 6.0 Unicode with EHP 4.0
- SAP ECC 6.0 with EHP 7.0 and all EHP previous versions
- SAP ECC 6.0 with EHP 7.5
- SAP ECC 6.0 with EHP 8.0

### SAP Client

- SAP .NET Connector (NCo) 3.0

### Oracle Database

- Oracle database 12.1
- Oracle database 18c (18.3)
- Oracle database 19c (19.3)

> [!IMPORTANT]
> Starting with version 18c, Oracle made some changes to the underlying metadata views that can impact clients that rely on those views, like BizTalk.  Due to these changes, there may be some scenarios where BizTalk may have consistent failures when interacting with Oracle 18c and 19c.
> 
> To address these scenarios, the Oracle packages used by BizTalk need to be reverted back to the Oracle 12.1 metadata format and recompiled.  Information about this metadata change and workaround are outlined in the [Oracle documentation](https://docs.oracle.com/en/database/oracle/oracle-database/18/upgrd/feature-changes-oracle-database-18c-upgrade.html#GUID-543498D6-3799-4217-9BE3-4BB8630FC32D) (opens Oracle's website).  Implementing this workaround in Oracle is fully supported by BizTalk, and does not require any additional configuration within BizTalk.

### Oracle Client

- Oracle Database 12.1 Client
- Oracle Database 18c Client (18.3)
Oracle Database 19c Client (19.3)

### Oracle E-Business Suite

- Oracle EBS 12.1
- Oracle EBS 12.1.3
- Oracle EBS 12.2.5

### Siebel Server

- Siebel 17

### Sieble Client

- Siebel Web Client 17

### SQL Server

- SQL Server 2014
- SQL Server 2016
- SQL Server 2017
- SQL Server 2019
- Azure SQL Database

> [!IMPORTANT]
> This version refers to the SQL Server versions used by the WCF-SQL adapter in BizTalk Server 2020. For the SQL Server versions supported as the back-end system to BizTalk Server, see [Hardware and Software Requirements for BizTalk Server 2020](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2020.md).

## Supported Enterprise systems

### JD Edwards Enterprise One

JD Edwards EnterpriseOne Application Release:

- 9.2
- 9.1

JD Edwards EnterpriseOne Tools Release:

- 9.2
- 9.1

### People Soft Enterprise

- PeopleSoft Enterprise Application Release 9.0
- PeopleSoft Enterprise Tools Release 8.49

### TIBCO Rendezvous

- TIBCO Rendezvous 8.4.6
- TIBCO Rendezvous Client 8.4.3

### TIBCO Enterprise Message Service

- 8.5

> [!IMPORTANT]
> Starting with BizTalk Server 2020 and newer, the TIBCO Enterprise Message Service Adapter is supported only in a 64-bit host.

### Updates for Enterprise Adapters

Fixes and product improvements are included in cumulative updates for the Enterpise Adapters. For more information, see [KB 4598360: Cumulative Update for BizTalk Server 2020 - Adapters for Enterprise Applications](https://support.microsoft.com/help/4598360/cu-for-biztalk-server-2020-adapters-for-enterprise-applications).

## Next steps

Get started with the [adapters and accelerators in BizTalk Server](../adapters-and-accelerators/adapters-and-accelerators-in-biztalk-server.md).
