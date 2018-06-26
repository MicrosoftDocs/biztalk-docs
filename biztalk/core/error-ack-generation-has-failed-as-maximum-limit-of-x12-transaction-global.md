---
title: "Error-Ack generation has failed as maximum limit of X12 transaction-global | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8bbcae14-6e5c-4f79-87c6-311b4b54c7ff
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error-Ack generation has failed as maximum limit of X12 transaction-global
## Details  
  
|                 |                                                                                                                                                                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                  |
| Product Version |                                                                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                              |
|    Event ID     |                                                                                                                          -                                                                                                                          |
|  Event Source   |                                                                                                                 BizTalk Server EDI                                                                                                                  |
|    Component    |                                                                                                                     EDI Engine                                                                                                                      |
|  Symbolic Name  |                                                                                                                          -                                                                                                                          |
|  Message Text   | Acknowledgement generation has failed as max limit of acceptable X12 transaction set control number has reached for Guest settings. Reset counter by navigating to Global configuration sender role screen, field ST 2 in Partner Agreement manager |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the X12 interchange because the control number that it entered in the Transaction set control number (ST2) of the acknowledgment is greater than the maximum value allowed for ST2. In this instance, BizTalk Server used the EDI global properties to create the acknowledgment.  
  
 The maximum value of the transaction set control number depends upon the number of digits used for the control number. The maximum length of all three fields is 9; the maximum length of the prefix and suffix fields is 8.  
  
## User Action  
 To resolve this error, reset the control number field (ST2.2) of the Transaction set control number (ST2) in the GS and ST Segment Definition Page to a value that is lower than the maximum limit. Set this property in the EDI Global Properties dialog box in the BizTalk Server Administration Console.