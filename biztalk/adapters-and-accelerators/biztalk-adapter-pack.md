---
title: "BizTalk Adapter Pack overview | Microsoft Docs"
description: See an overview of all the adapters included in the BizTalk Adapter Pack, including Oracle database and e-business suite, SAP, Siebel, and SQL Server in BizTalk Server.
ms.custom: "biztalk-2020"
ms.date: "01/13/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1960a5a-d627-42ce-8898-5df444846fea
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "mijacobs"
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

### BizTalk Server 2020 and newer

Starting with **BizTalk Server 2020** and newer, all BizTalk Adapter Pack features, including the SDK, are included with BizTalk Server 2020 installation. A separate installation of BizTalk Adapter Pack or WCF LOB Adapter SDK isn't required.

Installing the BizTalk Developer Tools/SDK and BizTalk Server Visual Studio Extension also installs the WCF LOB Adapter SDK.

Installing the BizTalk Server Runtime and Windows Communication Foundation adapters installs all adapters included in the BizTalk Adapter Pack.

The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] is included with BizTalk Server.

### Other versions

- [Install BizTalk Adapter Pack 2016](../adapters-and-accelerators/install-the-biztalk-adapter-pack-2016.md).
- [Install BizTalk Adapter Pack 2013 R2 and 2013](../adapters-and-accelerators/install-biztalk-adapter-pack-2013-r2-and-2013.md).

## FAQ

Get some answers to [Frequently asked questions](../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.yml) about the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].

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

- A **developer** using these adapters should be at least moderately experienced with:
  - Microsoft [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)], and the development of .NET solutions
  - Programming with the [!INCLUDE[btsDotNetFramework_md](../includes/btsdotnetframework-md.md)]
  - Programming with the [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)]
  - Extensible Markup Language (XML)
  - XML Schema Definition (XSD) language
  - Web Services Definition Language (WSDL)

- An **IT professional** using these should be at least moderately experienced with:
  - SQL Server Integration Services (SSIS)
  - Microsoft BizTalk Server
  - [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]

- **ISVs** using these adapters should be at least moderately experienced with:
  - The internal workings and concepts of each adapter, and be able to build applications on top of the adapters
  - [!INCLUDE[btsDotNetFramework_md](../includes/btsdotnetframework-md.md)]
  - The [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]

## See also

[Adapters and Accelerators in BizTalk Server](adapters-and-accelerators-in-biztalk-server.md)
