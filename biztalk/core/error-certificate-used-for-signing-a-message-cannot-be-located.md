---
title: "The certificate used for signing a message cannot be located in the local certificate store | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff3c7a2-954c-4c62-a7b2-06f7a38d61b3
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The certificate used for signing a message cannot be located in the local certificate store
## Details  
  
|                 |                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                    |
| Product Version |                                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                |
|    Event ID     |                                                            -                                                             |
|  Event Source   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                  |
|    Component    |                                                        AS2 Engine                                                        |
|  Symbolic Name  |                                                 CertificateMissingError                                                  |
|  Message Text   | The certificate used for signing a message cannot be located in the local certificate store. Certificate thumbprint: {0} |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the signing certificate was not in the required certificate store.  
  
## User Action  
 To resolve this error, do the following:  
  
1.  Identify the signing certificate by opening the BizTalk Server Administration Console, right-clicking the BizTalk Group, and then clicking the Certificate node.  
  
2.  Open MMC, add the snap-in for the My user account, and then open the Certificates, Personal, and Certificates node.  
  
3.  Make sure that the Current User certificate store contains the private key for that signing certificate by looking for the thumbprint identified in the error message text.