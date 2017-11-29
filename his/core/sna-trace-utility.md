---
title: "SNA Trace Utility1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c05c1041-9a6e-4a44-8caa-8566a27584ba
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# SNA Trace Utility
If you are working to improve performance or solve a problem in Host Integration Server , you can use trace tools to determine the source of the problem. The following information guides you through configuring and using the [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] SNA Trace Utility. The SNA Trace Utility is used to control trace files.  
  
 A trace file contains a record of internal activities. When you enable the Trace utility, the Trace files are stored in the TRACES folder of the Host Integration Server folder. Trace files have the extension .ATF.  
  
 When gathering information about system difficulties, it is best to start with event log information. Event log information is generally more straightforward to interpret than tracing information. However, if you call product support, the technician may ask for some or all of the following information:  
  
-   Tracing. Trace files record activity between or within components of Host Integration Server. Trace files provide detailed information about the exact sequence of events occurring within Host Integration Server or between Host Integration Server and another system on the network. Tracing is turned on in Host Integration Server using the SNA Trace tool, which is located in the Applications and Tools program group of Host Integration Server. Trace files are created in the TRACES folder of the root folder with the filename extension .ATF.  
  
-   Windows Server event logs. When gathering information about system difficulties, it is generally best to start with the event logs, which record system and application events, including errors. Event logs are more straightforward to interpret than tracing information. Use tracing information if the event logs do not provide enough detail.  
  
 The Trace utility is started from SNA Manager, or the Trace icon in the Host Integration Server Applications and Tools program group. You can run the Trace utility on each server in the subdomain. For specific instructions on running traces, see the Host Integration Server online Help.  
  
 After you start the Trace utility in Host Integration Server or on a Host Integration Server client, you can enable or disable trace options.  
  
 Use the topics in this section to navigate through the Trace Utility User Interface. Click a topic below for more information.  
  
## In This Section  
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals.md)  
  
 [Running the SNA Trace Utility](../core/running-the-sna-trace-utility.md)  
  
 [Trace Utility Help](../core/trace-utility-help.md)