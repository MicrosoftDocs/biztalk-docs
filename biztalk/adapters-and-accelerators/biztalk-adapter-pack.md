---
title: "BizTalk Adapter Pack | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1960a5a-d627-42ce-8898-5df444846fea
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Adapter Pack
## Overview
 The Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] includes adapters that enable enterprise applications and databases to interface with each other by using a common adapter framework. Similar to programming to web services, adapters enable clients to program to different enterprise applications. Technically, adapters are a binding to Windows Communication Framework (WCF). The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] includes the following adapters:  

- [!INCLUDE[adapteroracle](../includes/adapteroracle-md.md)] ([!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)])  

- [!INCLUDE[adapteroracleebusinesslong](../includes/adapteroracleebusinesslong-md.md)] ([!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)])  

- [!INCLUDE[adaptersap](../includes/adaptersap-md.md)] ([!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]). This also includes the [!INCLUDE[adoprovidersaplong](../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)])  

- [!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)] ([!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]). This also includes the [!INCLUDE[adoprovidersiebellong](../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)])  

- [!INCLUDE[adaptersql](../includes/adaptersql-md.md)] ([!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]).  

Using these adapters, you can connect to these on-premises line-of-business (LOB) systems to get data, and put data. The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and can be used or consumed from: 

* [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* A .NET application
* An ADO interface
* A Microsoft SharePoint portal

## Install BAP
The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] is included with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. For the specific installation steps, see:

* [Install BizTalk Adapter Pack 2016](../adapters-and-accelerators/install-the-biztalk-adapter-pack-2016.md)
* [Install BizTalk Adapter Pack 2013 R2 and 2013](../adapters-and-accelerators/install-biztalk-adapter-pack-2013-r2-and-2013.md)

## FAQ 
Get some answers to [Frequently asked questions](../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md) about the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].

## Oracle Database adapter
[Microsoft BizTalk Adapter for Oracle Database](../adapters-and-accelerators/adapter-oracle-database/microsoft-biztalk-adapter-for-oracle-database-documentation.md) includes information on the architecture, and how to use the adapter in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and the WCF service and channel models. Security, troubleshooting the adapter, and the adapter reference are also covered. 

## Oracle E-Business Suite adapter
[Microsoft BizTalk Adapter for Oracle E-Business Suite](../adapters-and-accelerators/adapter-oracle-ebs/microsoft-biztalk-adapter-for-oracle-e-business-suite-documentation.md) includes information on the architecture, and how to use the adapter in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and the WCF service and channel models. Security, troubleshooting the adapter, and the adapter reference are also covered. 

## SAP adapter
[Microsoft BizTalk Adapter for mySAP Business Suite](../adapters-and-accelerators/adapter-sap/microsoft-biztalk-adapter-for-mysap-business-suite-documentation.md) includes information on the architecture, and how to use the adapter in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and the WCF service and channel models. Security, troubleshooting the adapter, and the adapter reference are also covered. 

## Siebel adapter
[Microsoft BizTalk Adapter for Siebel eBusiness Applications](../adapters-and-accelerators/adapter-siebel/microsoft-biztalk-adapter-for-siebel-ebusiness-applications-documentation.md) includes information on the architecture, and how to use the adapter in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and the WCF service and channel models. Security, troubleshooting the adapter, and the adapter reference are also covered. 

## SQL adapter 
[Microsoft BizTalk Adapter for SQL Server](../adapters-and-accelerators/adapter-sql/microsoft-biztalk-adapter-for-sql-server-documentation.md) includes information on the architecture, and how to use the adapter in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and the WCF service and channel models. Security, troubleshooting the adapter, and the adapter reference are also covered. 

## WCF LOB adapter SDK
Use the [WCF Line of Business Adapter SDK](../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md) to create your own service-oriented interfaces to existing LOB systems. 

## Who should use the BizTalk Adapter Pack?

The potential users for the BizTalk Adapter Pack include:  

- Developers who directly program to the adapters

- IT professionals who consume the adapters using other integration platforms, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]

- Independent software vendors (ISVs) who build solutions on top of the adapters  

Suggested skills and knowledge for these roles include: 


|                                                                                                                                                                                                                                                                              Developer recommendation                                                                                                                                                                                                                                                                              |                                                                                                                                                                  IT pro recommendation                                                                                                                                                                  |                                                                                                                                                                                ISV recommendation                                                                                                                                                                                 |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A developer using these adapters should be at least moderately experienced with:<br/> <ul><li>Microsoft [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)], and the development of .NET solutions</li><li>Programming with the [!INCLUDE[btsDotNetFramework_md](../includes/btsdotnetframework-md.md)] </li><li>Programming with the [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] </li><li>Extensible Markup Language (XML) </li><li>XML Schema Definition (XSD) language </li><li>Web Services Definition Language (WSDL) </li></ul> | An IT professional using these should be at least moderately experienced with: <br/><ul><li>SQL Server Integration Services (SSIS) </li><li>Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] </li><li>[!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] </li></ul> | ISVs using these adapters should be at least moderately experienced with: <br/><ul><li>The internal workings and concepts of each adapter, and be able to build applications on top of the adapters </li><li>[!INCLUDE[btsDotNetFramework_md](../includes/btsdotnetframework-md.md)] </li><li>The [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] </li></ul> |

