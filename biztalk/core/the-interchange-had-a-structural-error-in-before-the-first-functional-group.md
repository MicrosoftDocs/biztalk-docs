---
title: "The interchange had a structural error in-before the first functional group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12202148-0a32-464e-8dbd-d01b9ba530eb
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The interchange had a structural error in-before the first functional group
## Details  
  
|                 |                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                        |
| Product Version |                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                    |
|    Event ID     |                                                                -                                                                 |
|  Event Source   |                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                      |
|    Component    |                                                            EDI Engine                                                            |
|  Symbolic Name  |                                           X12InterchangeStructuralErrorBefore1stGroup                                            |
|  Message Text   | The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error in/before the first functional group |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, for one of the following reasons:  
  
-   A structural error occurred in either the ISA and IEA segments or the first functional group of the interchange, so the interchange did not conform to the applicable schema.  
  
-   The X12ServiceSchema (in BaseArtifacts.dll) was not deployed.  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   Have the sender of the interchange change the ISA and/or IEA segments or the first functional group so that it conforms to the applicable schema, and then resend the interchange.  
  
-   Ensure that BaseArtifacts.dll includes the X12ServiceSchema and is deployed. You can do so by opening the BizTalk Server Administration Console, opening the BizTalk EDI Application node and the Schemas node, and verifying that X12ServiceSchema is listed.