---
title: "About the .NET Framework Data Provider for mySAP Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSIS"
  - "EXEC query"
  - "SELECT query"
  - "SAPDiscoveredObjects.xml"
  - "SQL Server Integration Services"
  - ".NET Framework Data Provider for mySAP Business Suite"
  - "Data Provider for SAP"
  - "custom RFC"
  - "Visual Studio DDEX plug-in"
ms.assetid: 4832f789-c1d8-4c5d-a49d-b1da6b7d4bd4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About the .NET Framework Data Provider for mySAP Business Suite
This section provides information about the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) and its features. For instructions about how to use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md).  
  
> [!NOTE]
>  Even if you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, your [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] is still incomplete until you install a custom RFC in the SAP system. For instructions on how to install the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
 You can use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] in the following ways:  
  
- To write an ADO.NET client to connect to the SAP system. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] exposes certain classes that enable you to interface with the provider.  
  
- To execute a SELECT query on the SAP system. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses the custom RFC for this feature.  
  
- To execute an EXEC operation on the SAP system. You can use this operation to perform queries on the SAP system.  
  
- To execute an EXECQUERY operation on the SAP system. You can use this operation to execute queries that are already defined in the SAP system.  
  
- To, in turn, use the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in to surface tables and function modules from the SAP system. The names of the objects discovered from the SAP system are written to a configuration file, SAPDiscoveredObjects.xml.  
  
- To use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Integration Services (SSIS).  
  
- To use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Reporting Services (SSRS).  
  
  For more information about performing these tasks, see [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md). For more information about the custom RFC, the SAPDiscoveredObjects.xml configuration file, and the limitations associated with the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see the following links.  
  
## In This Section  
  
-   [Custom RFCs Used by the Provider in SAP](../../adapters-and-accelerators/adapter-sap/custom-rfcs-used-by-the-provider-in-sap.md)  
  
-   [About the SAPDiscoveredObjects.xml File in SAP](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md)  
  
-   [Limitations of the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/limitations-of-the-net-framework-data-provider-for-mysap-business-suite.md)