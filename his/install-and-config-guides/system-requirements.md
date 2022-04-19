---
description: "Learn more about: System Requirements"
title: "Host Integration Server 2016 system requirements | Microsoft Docs"
ms.custom: ""
ms.date: 02/10/2020
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af7d5928-5e99-4c03-afc0-16330e5f207c
caps.latest.revision: 9
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---

# System Requirements for Host Integration Server 2016

These system requirements list the installation, configuration, and feature usage prerequisites for Host Integration Server 2016.

## Requirements

| Category | Minimum requirement |
|---|---|
| Hardware |-   Computer or virtual hard drive (VHD) with 64-bit X64 architecture processor<br />-   6GB of available drive space<br />-   800 x 600 screen resolution for administration tools<br />-   1024 x 768 resolution for visual design tools |
| Operating Systems | -   Windows Server 2019 (requires HIS 2016 CU3)<br />-   Windows Server 2016<br />-   Windows Server 2012 R2<br />-   Windows 10<br />-   Windows 8.1<br />-   Virtualization with Azure and Hyper-V  |
|  .NET Framework  | Microsoft .NET Framework 4.6 using the [Web installer](https://go.microsoft.com/fwlink/p/?LinkId=528259) (<https://go.microsoft.com/fwlink/p/?LinkId=528259>) **OR** the [off-line installer](https://go.microsoft.com/fwlink/p/?LinkId=528233) (<https://go.microsoft.com/fwlink/p/?LinkId=528233>).  |
|  Visual Studio  | The HIS designer supports the following Visual Studio versions:<br /><br /> -   Visual Studio 2015<br /> -   Visual Studio 2013 with Update 5 |
| BizTalk Adapters and Tools | Supported BizTalk Server versions:<br /><br />-   BizTalk Server 2020 (requires HIS 2016 CU3)<br />-   BizTalk Server 2016<br />-   BizTalk Server 2013 R2  |
| Data Integration |  Data integration clients and DRDA Service support the following SQL Server versions:<br /><br />-   SQL Server 2019 (requires HIS 2016 CU3)<br />-   SQL Server 2017 (requires HIS 2016 CU3)<br />-   SQL Server 2016<br />-   SQL Server 2014<br />-   SQL Server 2012 |
| WCF Channel for MQ and BizTalk adapter for MQ Series Client (MQSC) | Supported IBM WebSphere versions to configure the WCF Channel for MQ and BizTalk Adapter for MQSC:<br /><br /> -   IBM MQ 9 (requires HIS 2016 CU3)<br />-   IBM MQ 8<br />-   IBM MQ 7.5 (client, extended client, server) |
| IBM operating systems | Supported IBM OS' to use the network integration features, including SNA services and terminal emulators:<br /><br /> -   IBM z/OS 2.3 (requires HIS 2016 CU3)<br />-   IBM z/OS 2.2<br />-   IBM z/OS 2.1<br />-   IBM z/VM 6.3<br />-   IBM z/VM 6.2<br />-   IBM z/VSE 6.2<br />-   IBM z/VSE 6.1<br />-   IBM i 7.3 (requires HIS 2016 CU3)<br />-   IBM i 7.2<br />-   IBM i 7.1 |
| IBM transaction processing systems | Supported IBM transaction processing systems to use the Transaction Integrator and BizTalk Adapter for Host Applications:<br /><br /><br /> -   IBM CICS 5.4 (requires HIS 2016 CU3)<br />-   IBM CICS 5.3<br />-   IBM CICS 5.2<br />-   IMS 15.1<br />-   IMS 14.1<br />-   IMS 13.1<br />-   IBM i 7.3 (requires HIS 2016 CU3)<br />-   IBM i 7.2<br />-   IBM i 7.1 |
| IBM message processing systems | Supported IBM message processing systems to use the WCF Channel for WebSphere MQ and BizTalk Adapter for MQSC:<br /><br /> -   IBM MQ 9.0 (requires HIS 2016 CU3)<br />-   IBM MQ 8.0<br />-   IBM MQ 7.5 |
| IBM file systems | Supported IBM host files systems to use the ADO.NET provider for Host files and BizTalk Adapter for Host files:<br /><br /> -   IBM DFSMS DFM for z/OS 2.3 (requires HIS 2016 CU3)<br />-   IBM DFSMS DFM for z/OS 2.2<br />-   IBM DFSMS DFM for z/OS 2.1<br />-   IBM i 7.3 (requires HIS 2016 CU3)<br />-   IBM i 7.2<br />-   IBM i 7.1 |
| IBM relational database management systems  | Supported IBM relational database management systems to use the DB2 and Informix clients (OLE DB, ADO.NET, BizTalk Adapter):<br /><br /> -   IBM DB2 for z/OS 12 (requires HIS 2016 CU3)<br />-   IBM DB2 for z/OS 11<br />-   IBM DB2 for z/OS 10<br />-   IBM DB2 for i 7.3<br />-   IBM DB2 for i 7.2<br />-   IBM DB2 for i 7.1<br />-   IBM DB2 for LUW 11.5 (requires HIS 2016 CU3)<br />-   IBM DB2 for LUW 11<br />-   IBM DB2 for LUW 10.5<br />-   IBM Informix 12.1<br />-   IBM Informix 11.7<br /><br /> Supported IBM relational database management systems to use the Service for DRDA:<br /><br /> -   IBM DB2 for z/OS 12 (requires HIS 2016 CU3)<br />-   IBM DB2 for z/OS 11<br />-   IBM DB2 for z/OS 10<br />-   IBM DB2 for i 7.3<br />-   IBM DB2 for i 7.2<br />-   IBM DB2 for i 7.1 |

## Next steps

[Install HIS](installing-his-2016.md) or [migrate from a previous version](his-migration-tool.md).
