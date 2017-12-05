---
title: "Host Platforms for DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb212530-7dde-4ea7-8d8f-41e4d7cb5688
caps.latest.revision: 4
---
# Host Platforms for DB2
IBM and other software vendors have implemented Distributed Relational Database Architecture (DRDA) support into database systems, such as IBM DB2, and database tools on a wide range of operating systems. DRDA is an open, published, and widely supported protocol, which requires no additional license for development. This makes DRDA appealing to independent software vendors (ISVs), solution providers, large corporate development groups, as well as their customers.  
  
 The OLE DB Provider for DB2 is implemented as an IBM DRDA application requester, which means it connects to popular DRDA-compliant DB2 systems.  
  
 The Microsoft OLE DB Provider for DB2 can access DB2 systems through SNA LU 6.2 using Microsoft Host Integration Server, and can access DB2 systems directly using TCP/IP, depending on the IBM DB2 platform and version.  
  
## OLE DB Environment  
 Three main roles are performed by software applications in an OLE DB environment:  
  
-   **OLE DB Consumer**. The end-user or server-based program that uses (consumes) the OLE DB interfaces. An example is a Web-based component that makes OLE DB calls to integrate host records with a Web-based report. Other examples include Excel and SQL Server Integration Services.  
  
-   **OLE DB Data Provider**. A driver or other program that exposes OLE DB interfaces for use by consumer applications. Data providers translate OLE DB interfaces to a language or commands that the target data source understands. An example is the OLE DB Provider for DB2, which translates OLE DB interfaces to distributed relational database architecture (DRDA) commands.  
  
-   *OLE DB Service Provider*. An application that both uses (consumes) and exposes OLE DB interfaces. Service providers typically act as proxies for the consumer, retrieving the data through the data provider and offering services to the consumer by manipulating the target data. Examples include resource pooling or a query-processing engine.  
  
## See Also  
 [OLE DB Provider for DB2 Programmer's Guide](../core/ole-db-provider-for-db2-programmer-s-guide.md)