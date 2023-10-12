---
description: "Learn more about: Connect to an SAP system using the adapter"
title: "Connect to an SAP system using the adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Connect to an SAP system using the adapter
The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI) to connect to the SAP system. With a connection URI, adapter clients can specify connection parameters to connect to an external system.For more information about the connection URI, see [Create a connection to the SAP system](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).  
  
 Make sure you comply with the security guidelines when establishing a connection with an SAP system. For more information about security guidelines, see [Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md).
  
## How Many Connections Can the Adapter Open to the SAP System?  
 By default, the SAP system enables clients to open 100 connections to the SAP system. However, you can set an environment variable on the computer running the SAP system to increase the limit on the number of connections. For more information, see [Troubleshoot Operational Issues with the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md).  
  
## See Also  
 [Architecture overview of the BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)
