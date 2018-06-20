---
title: "The agreement associated with BatchId is not enabled or has expired. Batching cannot continue | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d92cb07-7646-42b3-90a8-18acbcd145cd
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The agreement associated with BatchId is not enabled or has expired. Batching cannot continue
## Details  
  
|                 |                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------|
|  Product Name   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| Product Version |                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    Event ID     |                                                 -                                                  |
|  Event Source   |       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI       |
|    Component    |                                             EDI Engine                                             |
|  Symbolic Name  |                                    ErrorBatchAgreementDisabled                                     |
|  Message Text   | The agreement associated with BatchId {0} is not enabled or has expired. Batching cannot continue. |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was not able to start a batch or process a batch message because of Agreement getting expired.  
  
## User Action  
 To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and its start and end date fall within the start and end dates of the Agreement. Also make sure that the agreement is enabled.