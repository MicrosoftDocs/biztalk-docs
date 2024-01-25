---
description: "Learn more about: The AS2 Decoder encountered an exception during processing"
title: "The AS2 Decoder encountered an exception during processing"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The AS2 Decoder encountered an exception during processing
## Details  
  
| Field | Error Details|
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                         |
| Product Version |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                     |
|    Event ID     |                                                                                                 -                                                                                                 |
|  Event Source   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                       |
|    Component    |                                                                                            AS2 Engine                                                                                             |
|  Symbolic Name  |                                                                          AS2DecoderExceptionEncounteredDuringProcessing                                                                           |
|  Message Text   | The AS2 Decoder encountered an exception during processing.  Details of the message and exception are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" MessageType: "{3}" Exception:"{4}" |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming AS2 message because of an issue with the AS2 Decoder.  
  
## User Action  
 To resolve this error, determine the nature of the error condition by checking the AS2 error code. For more information on AS2 error codes, see the "AS2 Error Codes" topic in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] help file.
