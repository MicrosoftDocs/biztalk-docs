---
description: "Learn more about: The AS2 Decoder failed processing when validating the MIC value returned in the MDN"
title: "The AS2 Decoder failed processing when validating the MIC value returned in the MDN"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The AS2 Decoder failed processing when validating the MIC value returned in the MDN
## Details  
  
|  Field               |  Error Details                                                                                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                           |
| Product Version |                                                                      [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                       |
|    Event ID     |                                                                                                   -                                                                                                   |
|  Event Source   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                         |
|    Component    |                                                                                              AS2 Engine                                                                                               |
|  Symbolic Name  |                                                                                AS2DecoderMdnMicFailureDuringProcessing                                                                                |
|  Message Text   | The AS2 Decoder failed processing when validating the MIC value returned in the MDN.  Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming MDN because the MIC (Message Integrity Check) failed validation.  
  
## User Action  
 To resolve this error, verify that the algorithm used for generating the MDN (in the Signed-Receipt-MICalg header of the original message) is the same as the algorithm specified in the Signed-Receipt-MICalg property for the AS2 Message Receiver. Both should be either SHA1 or MD5. If the algorithm specified is the same, verify that Received-Content-MIC extension field in the second part of the multipart signed MDN message includes a valid MIC digest. If it does, determine why the MDN does not correspond to the interchange that was sent.
