---
description: "Learn more about: The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header"
title: "The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header
## Details  
  
|   Field         |                                      Error Details                                                                          |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                      |
| Product Version |                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                  |
|    Event ID     |                                                              -                                                              |
|  Event Source   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                    |
|    Component    |                                                         AS2 Engine                                                          |
|  Symbolic Name  |                               AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError                                |
|  Message Text   | The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header which is required for MDN generation. |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN because the incoming AS2 message did not include the Disposition-Notification-Options header that indicates whether the MDN must be signed and which MIC algorithm must be used.  
  
## User Action  
 To resolve this error, have the sender of the AS2 message include the Disposition-Notification-Options header in the message and then resend the message.
