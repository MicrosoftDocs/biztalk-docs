---
title: "Siebel adapter samples | Microsoft Docs"
description: Siebel WCF adapter samples that can be used with BizTalk Server, WCF service model, and the Data Provider for Siebel
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 069d676e-211e-474c-9cf5-c660fdd22014
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Samples for the Siebel adapter
Samples for [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] are categorized into:  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] samples  

- WCF service model samples  

- [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] samples  


The samples are available at [BizTalk Adapter Pack 2010: Siebel adapter samples](https://www.microsoft.com/download/details.aspx?id=6492). 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]

The following list describes the samples.

## BizTalk Server samples  

|      Sample Directory Name      |                                                                                     Description                                                                                     |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         BusinessService         |                    Demonstrates how to invoke a business service in Siebel using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].                     |
|             MVLDemo             |                Demonstrates how to work with multivalue links (MVLs) in Siebel using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].                 |
|          SiebelAccount          |        Demonstrates how to insert records into the Account business component in Siebel using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].        |
| SiebelAdapterIntegrationObjects | Demonstrates how to invoke a business service in Siebel, which works with Integration Objects, using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. |
|         SiebelPicklist          |      Demonstrates how to insert values of picklist types into a Siebel business component using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].      |

## WCF service model samples 

|Sample Directory Name|Description|  
|---------------------------|-----------------|  
|AccountInsertDelete|Demonstrates how to perform Insert, Update, Delete, and Query operations on a Siebel business component. The sample inserts a record into the Account business component of the Account business object, updates the record, and finally deletes it. Before and after each operation a Query operation is performed on the business component to verify the results.|  
|Business Services|Demonstrates how to invoke a Siebel business service method, TimeStamp, and displays the results to the console.|  
|MVL|Demonstrates how to work with multivalue links in a Siebel business component by using the Associate, Dissociate, and child query operations. The sample displays all contacts associated with an account. It also shows how to Associate and Dissociate a contact from an account.|  

## Data Provider for Siebel sample  

| Sample Directory Name |                                                Description                                                 |
|-----------------------|------------------------------------------------------------------------------------------------------------|
|      siebel ado       | Demonstrates how to use the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]. |

## See Also  
[Develop your Siebel applications](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)