---
title: "Capturing Problems through Tracing | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6667a166-cfc1-426d-a71a-1ecf01b8b6ac
caps.latest.revision: 3
---
# Capturing Problems through Tracing
There are multiple options for tracing, which can help to capture problems in the consumer, service components, provider, networking and host data source.  
  
 **SQL consumer tracing using SQL Server Profiler**  
  
 SQL Server Profiler is a graphical user interface to SQL Trace for monitoring an instance of the Database Engine or Analysis Services. You can capture and save data about each event to a file or table to analyze later. For more information, see [Introducing SQL Server Profiler](http://go.microsoft.com/fwlink/?LinkID=180433) (http://go.microsoft.com/fwlink/?LinkID=180433).  
  
 **Data provider tracing using Provider Trace Utility**  
  
 The HIS Trace Utility captures and saves information from the Microsoft network client connections, provider interfaces and data messages. For more information, see [Trace Utility Help](../core/trace-utility-help2.md) and [SNA Trace Utility](../core/sna-trace-utility2.md).  
  
 **Network tracing using Network Monitor**  
  
 The Network Monitor captures network traffic for display and analysis. It enables you to perform tasks such as analyzing previously captured data in user-defined methods, extracting data from defined protocol parsers. It includes a Distributed Data Management (DDM) parser for use with the HIS data network clients. Contact Microsoft Customer Support Services for a copy of the DDM parser. For more information, see [Network Monitor](http://go.microsoft.com/fwlink/?LinkID=180448) (http://go.microsoft.com/fwlink/?LinkID=180448).  
  
 **DB2 server tracing using IBM tools**  
  
 For more information, see the IBM DB2 Administration Guide for the applicable DB2 platform and version.  
  
 **Windows Server events using Event Viewer**  
  
 The Event Viewer is a Microsoft Management Console (MMC) snap-in that enables you to browse and manage event logs. For more information, see [Event Viewer](http://go.microsoft.com/fwlink/?LinkID=131274) (http://go.microsoft.com/fwlink/?LinkID=131274).  
  
## See Also  
 [Data Integration (Troubleshooting)](../core/data-integration-troubleshooting-1.md)