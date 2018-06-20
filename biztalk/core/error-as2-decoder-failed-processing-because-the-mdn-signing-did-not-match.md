---
title: "The AS2 Decoder failed processing because the MDN signing did not match our request | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a42d344-fc28-4bc4-9328-46158f15a008
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The AS2 Decoder failed processing because the MDN signing did not match our request
## Details  
  
|                 |                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                           |
| Product Version |                                                                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                       |
|    Event ID     |                                                                                                   -                                                                                                    |
|  Event Source   |                                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                         |
|    Component    |                                                                                               AS2 Engine                                                                                               |
|  Symbolic Name  |                                                                          AS2DecoderMdnSigningMismatchFailureDuringProcessing                                                                           |
|  Message Text   | The AS2 Decoder failure processing because the MDN signing did not match our request.  Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming MDN either because the MDN was signed, but signing wasn't requested for the MDN, or the MDN was unsigned, but signing was requested for the MDN.  
  
## User Action  
 To resolve this error, do one of the following:  
  
1.  Change the signature request for the MDN to match the request. To do so, open the Party as AS2 Message Receiver page of the AS2 Properties dialog box, and with the "Request MDN" property selected, either select or clear the "Request signed MDN" property.  
  
2.  Contact the receiver of the original AS2 message to resolve whether MDNs should be signed or not.