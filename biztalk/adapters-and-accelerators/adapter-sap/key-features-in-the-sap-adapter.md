---
title: "Key features in the SAP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters, deprecated features"
  - "features, technology-related"
  - "adapters, new features"
  - "features, deprecated"
  - "features, metadata-related"
  - "librfc32u.dll"
  - "tRFC server"
  - "features, new"
  - "adapters, new and deprecated features"
  - "queued tRFC client calls"
  - "features, operations-related"
  - "RFC server"
ms.assetid: 30e3140c-447f-42ba-a3b0-13ae66e78b0c
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Key features in the SAP Adapter
This section lists the new and deprecated features in [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
> [!NOTE]
>  This topic has been used from the previous version of [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] Help.  
  
## Features in the SAP Adapter  
 The following are the features introduced in the previous releases of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### Technology-Related Features  
  
|                                                            Feature                                                             |                                                                                                                                                                                                                                                                                              Comment                                                                                                                                                                                                                                                                                               |
|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SQL Server Reporting Services (SSRS). | Client programs can now use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] to import data from an SAP backend into an SSRS project and generate reports out of the data. For more information on how to use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] with SSRS, see [Use the Data Provider for SAP with SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssrs.md). For more information about SSRS, see [SQL Server Reporting Services](https://msdn.microsoft.com/library/ms159106.aspx). |
|                                     Support for invoking queries defined in an SAP system                                      |                                                                                                                                                           The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] exposes an operation, EXECQUERY, that can be used to execute queries defined in an SAP system. For more information on how to use the EXECQUERY feature, see [Support for Executing SAP Queries                                                                                                                                                            |

](https://msdn.microsoft.com/library/dd788118.aspx).|  
|Support for using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft Office SharePoint Server (MOSS)|You can use the adapters to present data from the SAP system onto a MOSS portal. For more information, see [Use the SAP Adapter with SharePoint](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md).|  
  
### Metadata-Related Features  
  
|                Feature                 |                                                                                                                                                                                                                                                                                                   Comment                                                                                                                                                                                                                                                                                                    |
|----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DataTypesBehavior** binding property | The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] provides a complex binding property, **DataTypesBehavior**, that enables adapter clients to control the adapter behavior when special values are encountered in the SAP system. For a detailed discussion about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md). |
  
### Operations-Related Features  
  
|                          Feature                          |                                                                                                                                                                                                                                                 Comment                                                                                                                                                                                                                                                  |
|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Support for invoking external programs required by an RFC | The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] provides a binding property, **RfcAllowStartProgram** that can be set to enable the RFC client library to invoke external programs, if any, required by a particular RFC. For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md). |
|    Support for sending multiple IDOCs in a single call    |                                                                                                                                                                                                      The SAP adapter now supports sending multiple IDOCs of the same type in a single adapter call.                                                                                                                                                                                                      |
  
### Other Features  
  
|                                                        Feature                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| New way of using the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] | The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-SAP port. If you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default. However, if you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-SAP port, you must first add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For more information, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md). |
  
## Deprecated Features in the SAP Adapter  
 The following sections lists the features that were supported in the previous version of the adapter, but which are not supported in the current version of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### EnableBusinessObjects binding property deprecated  
 This binding property was deprecated in [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. This binding property was used to determine whether the BAPI node is displayed while generating metadata while using [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
## See Also  
 [Understand BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)