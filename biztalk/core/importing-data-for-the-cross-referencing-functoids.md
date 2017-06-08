---
title: "Importing Data for the Cross Referencing Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, about BizTalk Server Cross Reference Import tool"
  - "CrossReferencing functoids"
  - "btsxrefimport.exe"
  - "Cross Reference Import tool, how to"
  - "Cross Reference Import tool"
  - "Database functoids, cross-referencing"
ms.assetid: 9eb847a6-bc9c-4459-8c8b-c7286c69c642
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Data for the Cross Referencing Functoids
The cross referencing database functoids use data from tables stored in the **BizTalkMgmtDb** SQL Server database. The Configuration Wizard creates the necessary tables in the database during installation. The tables are, however, initially empty.  
  
 The BizTalk Server Cross Reference Import tool (btsxrefimport.exe) reads data from a group of nine XML documents and stores the data in the appropriate tables.  
  
> [!NOTE]
>  You must populate the tables in order to use the cross referencing functoids (**Format Message**, **Get Application ID**, **Get Application Value**, **Get Common ID**, **Get Common Value**, **Remove Application ID**, and **Set Common Value**).  
  
 This section describes how to the use the tool, and the format of each of the required XML documents.  
  
## In This Section  
  
-   [BizTalk Server Cross Reference Import Tool (BTSXRefImport.exe)](../core/biztalk-server-cross-reference-import-tool-btsxrefimport-exe.md)  
  
-   [SetUp-Files Document](../core/setup-files-document.md)  
  
-   [listOfAppType Document](../core/listofapptype-document.md)  
  
-   [listOfAppInstance Document](../core/listofappinstance-document.md)  
  
-   [listOfIDXRef Document](../core/listofidxref-document.md)  
  
-   [listOfIDXRefData Document](../core/listofidxrefdata-document.md)  
  
-   [listOfValueXRef Document](../core/listofvaluexref-document.md)  
  
-   [listOfValueXRefData Document](../core/listofvaluexrefdata-document.md)  
  
-   [listOfMessageDef Document](../core/listofmessagedef-document.md)  
  
-   [listOfMessageText Document](../core/listofmessagetext-document.md)