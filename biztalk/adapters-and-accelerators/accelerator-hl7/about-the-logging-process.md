---
title: "About the Logging Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "logging, about logging"
  - "auditing, about auditing"
  - "logging"
  - "auditing"
ms.assetid: 859ee1f5-aae4-4a47-ab39-8d2b4168a429
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About the Logging Process
Since your applications handle critical, time sensitive and monetary data, auditing becomes a critical part of the application. To enable enterprise level manageability and availability, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] relies on the following shared run time and administrative components:  
  
- **Logging**: to collect and route all log events in a managed way to a designated database  
  
- **Event Monitoring and Service Debugging**: to configure logging behavior and to investigate/manage collected information for system administrators and other IT professionals  
  
  With the enhanced auditing features in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], you can optimize your operational efficiency, security, and performance to ensure compliance with HL7 regulations.  
  
## Types of Data  
 This topic describes different types of logging data used by the logging feature and where this data is stored:  
  
- Configuration data: Logging configuration data is stored in the Configuration database (also known as the BizTalk Management database) and includes SQL auditing information and audit data ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Event viewer, centralized database WMI) location.  
  
- Archival data: The EventLog table in the SQL log stores the 'Logging' data.  
  
## How Logging Works  
 This topic describes the three types of events the software logs, as well as the three locations where you can store the logged data.  
  
|Component|Purpose|  
|---------------|-------------|  
|Configuration Editor|To specify where to save the log data. BTAHL7 supports logging to any combination of the following: Event Viewer, WMI, and SQL Server logging.|  
|Event Broker|To receive log events raised by other components and log them based on logging configuration data.|  
|Logging API|Logging interface called by all BTAHL7 assemblies.|  
  
### Types of Logging  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logs three types of errors:  
  
- Informational events, such a service started or stopped or an event failed.  
  
- Warning events such as non-critical errors and warnings in [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Event logs. For example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspends a message because data validation failed.  
  
- Error events for critical failures in a component. For example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspends a message because of parser failures.  
  
  The system can log [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] events into following configurable locations:  
  
- [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Event viewer  
  
- WMI events  
  
- Centralized database (SQL logging database)  
  
  An event broker receives all [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logging events and, based on the configuration information, sends them to the appropriate location.  
  
### Overview of Features  
 The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logging feature provides:  
  
-   A unified way of logging all the error messages  
  
-   A centralized repository for storing all event details  
  
-   A consistent object model for logging messages flowing to discrete line-of-business applications  
  
-   A combination of logging and tracing to help system administrators correlate logged errors with documents  
  
## Event Log Data  
 This topic describes the format and content of the event log data.  
  
 The following table shows typical logged data for partners.  
  
|Data|Description|  
|----------|-----------------|  
|LogData|Data log|  
|CategoryNumber|Category number|  
|EntryType|Type of the event|  
|EventId|Event ID|  
|MachineName|Computer name|  
|Message|Message detail|  
|Source|Creating, updating, reading, deleting, deploying, or archiving data|  
|TimeGenerated|Success or Failure|  
|UserName|User name|  
|MsgGuid|Message GUID|  
|SvcGuid|Service GUID|  
|Operation|Operation detail|  
  
## See Also  
 [Configuring Logging](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)