---
description: "Learn more about: The agreement associated with BatchId is not enabled or has expired. Batching cannot continue"
title: "The agreement associated with BatchId is not enabled or has expired. Batching cannot continue"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The agreement associated with BatchId is not enabled or has expired. Batching cannot continue
## Details  
  
| Field | Error Details |
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
