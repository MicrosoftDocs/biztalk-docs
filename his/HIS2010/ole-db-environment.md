---
title: "OLE DB Environment | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd7d92fa-2615-4472-b3b3-d2f71700b2af
caps.latest.revision: 4
---
# OLE DB Environment
Three main roles are performed by software applications in an OLE DB environment:  
  
-   **OLE DB Consumer.** The end-user or server-based program that uses (consumes) the OLE DB interfaces. An example is a Web-based component that makes OLE DB calls to integrate host records with a Web-based report. Other examples include Excel and SQL Server Integration Services.  
  
-   **OLE DB Data Provider.** A driver or other program that exposes OLE DB interfaces for use by consumer applications. Data providers translate OLE DB interfaces to a language or commands that the target data source understands. An example is the OLE DB Provider for AS/400 and VSAM, which translates OLE DB interfaces to distributed data management (DDM) record-level commands.  
  
-   **OLE DB Service Provider.** An application that both uses (consumes) and exposes OLE DB interfaces. Service providers typically act as proxies for the consumer, retrieving the data through the data provider and offering services to the consumer by manipulating the target data. Examples include resources pooling or a query-processing engine.