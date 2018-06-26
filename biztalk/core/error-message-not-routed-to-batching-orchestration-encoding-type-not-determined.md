---
title: "The message cannot be routed to the batching orchestration as the Encoding type could not be determined | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d2ee38d-22c0-4fcf-bb68-b2ef00088c4c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The message cannot be routed to the batching orchestration as the Encoding type could not be determined
## Details  
  
|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| Product Version |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    Event ID     |                                                                                              -                                                                                              |
|  Event Source   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    Component    |                                                                                       Batching Engine                                                                                       |
|  Symbolic Name  |                                                                                     UnknownEncodingType                                                                                     |
|  Message Text   | The message cannot be routed to the batching orchestration as the Encoding type could not be determined. The encoding type needs to be either X12 or EDIFACT for the message to be batched. |
  
## Explanation  
 This Error/Warning/Information event indicates that a non-EDI batch element was not routed to the batching orchestration instance, even though the transaction set meets the filter criteria for batching. The transaction set could not be routed to the batching orchestration instance because the EDI.EncodingType context property was not promoted with a value of 0 for X12 or 1 for EDIFACT. This error occurred when the batch element was routed by the BatchMarker pipeline component to the routing orchestration, but the non-EDI batch element was not converted by a map into an EDI message. As a result, the routing orchestration could not determine the encoding type from the EDI headers.  
  
## User Action  
 To resolve this error, make sure that the non-EDI message is converted by a map into an EDI message before it is routed to the routing orchestration. You must also include a custom pipeline component (with the BatchMarker component) or custom orchestration to process the non-EDI batch element. For more information, see "Assembling a Batched EDI Interchange" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.