---
description: "Learn more about: The Signing Certificate has not been configured for AS2 party"
title: "The Signing Certificate has not been configured for AS2 party"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The Signing Certificate has not been configured for AS2 party
## Details  
  
| Field | Error Details |
|-----------------|-------------------------------------------------------------------------------------------|
|  Product Name   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]     |
| Product Version |                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                 |
|    Event ID     |                                             -                                             |
|  Event Source   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI   |
|    Component    |                                        AS2 Engine                                         |
|  Symbolic Name  |                               SigningCertNotConfiguredError                               |
|  Message Text   | The Signing Certificate has not been configured for AS2 party.  AS2-From: {0} AS2-To: {1} |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the signing certificate was not configured for the group.  
  
## User Action  
 To resolve this error, configure signing certificate by doing the following:  
  
1.  Open the BizTalk Server Administration Console.  
  
2.  Move to the Group node, and click the Certificate node.  
  
3.  Enter the common name and thumbprint of the certificate.
