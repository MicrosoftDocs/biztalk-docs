---
description: "Learn more about: Data Clients Error Codes and Messages"
title: "Data Clients Error Codes and Messages"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Clients Error Codes and Messages
The Data Clients for DB2 and Informix connect to IBM DB2 and Informix databases using the Distributed Relational Database Architecture (DRDA) protocol and formats. Using a Network Monitor, you can trace the DRDA protocol code points (commands) and instance variables (command parameters) when connecting across a TCP/IP network. The DRDA protocol code points are published as an industry standard through Open Group. You can download DRDA V5 Vol. 1: Distributed Relational Database Architecture, publication number C112 and V5 Vol. 3: Distributed Data Management Architecture, publication number C114, published July 2011, from `http://www.opengroup/.org/dbiop`.  
  
 The Data Providers for DB2 and Informix return standard DB2 and Informix SQLSTATE and SQLCODE error codes with error message text. The DB2 and Informix error codes and messages are published by IBM at www.ibm.com.  
  
 The Data Client for Host Files uses the Distributed Data Management Record-Level Input/Output protocol and formats. Using a Network Monitor, you can trace the DDM protocol code points (commands) and instance variables (command parameters) when connecting across a TCP/IP network. Using the HIS 2013 managed tracing, you can trace the DDM RLIO code point reply messages. The DDM protocol code point reply messages are published by IBM at www.ibm.com.  
  
 The Data Provider for Host Files returns a provider-specific error code with error message text.  
  
## Error Types by Feature  
 The tables in this section break out Host Integration Server feature errors into separate tables organized by Data Client and Data Provider sources (DB2, Informix, and Host Files) and broken out by feature. The following sections contain error tables organized by protocol, network, security and transaction.  
  
## DB2  
  
|Feature|DRDA Protocol|SNA APPC Network|TCPIP Network|Security|Transaction|  
|-------------|-------------------|----------------------|-------------------|--------------|-----------------|  
|Entity Provider for DB2|x|x|x|X|x|  
|BizTalk Adapter for DB2|x|x|x|X|x|  
|ADO.NET Data Provider for DB2|x|x|x|X|x|  
|OLE DB Provider for DB2|x|x|x|X|x|  
|ODBC Driver for DB2|x|x|x|X|x|  
  
## Informix  
  
|Feature|DRDA Protocol|SNA Network|TCPIP Network|Security|Transaction|  
|-------------|-------------------|-----------------|-------------------|--------------|-----------------|  
|OLE DB Provider for DB2|x||x|x|x|  
  
## Host Files  
  
|Feature|RLIO Protocol|Client and Provider|  
|-------------|-------------------|-------------------------|  
|BizTalk Adapter for Host Files|x|x|  
|ADO.NET Data Provider for Host Files|x|x|
