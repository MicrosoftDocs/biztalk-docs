---
title: "The AS2 Decoder failed processing because the MDN indicated the AS2 message failed processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2bce620a-f336-435e-b7c3-3db060f2819d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The AS2 Decoder failed processing because the MDN indicated the AS2 message failed processing
## Details  
  
|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                |
| Product Version |                                                                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                            |
|    Event ID     |                                                                                                        -                                                                                                         |
|  Event Source   |                                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                              |
|    Component    |                                                                                                    AS2 Engine                                                                                                    |
|  Symbolic Name  |                                                                                      AS2DecoderMdnProcessingFailureReturned                                                                                      |
|  Message Text   | The AS2 Decoder failure processing because the MDN indicated the AS2 message failed processing.  Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the MDN response shows that the receiver of the original AS2 message could not process the original AS2 message.  
  
## User Action  
 To resolve this error, contact the receiver of the AS2 message, determine why processing failed at the receiver, fix the original AS2 message, and then resend.