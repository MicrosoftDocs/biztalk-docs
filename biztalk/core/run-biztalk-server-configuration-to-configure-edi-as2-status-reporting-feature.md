---
title: "To enable status reporting, run &#39;BizTalk Server Configuration&#39; and configure EDI-AS2 status reporting feature | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf125919-80ab-4cb8-b1f5-0f2616cc6f5c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# To enable status reporting, run &#39;BizTalk Server Configuration&#39; and configure EDI-AS2 status reporting feature
## Details  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  Product Name   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| Product Version |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    Event ID     |                                                       -                                                        |
|  Event Source   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI             |
|    Component    |                                                   EDI Engine                                                   |
|  Symbolic Name  |                                                       0                                                        |
|  Message Text   | To enable status reporting, run 'BizTalk Server Configuration' and configure EDI/AS2 status reporting feature. |
  
## Explanation  
 This Error/Warning/Information event indicates that EDI/AS2 status reporting is not working because it has not been configured.  
  
## User Action  
 To resolve this error, do the following:  
  
1.  Run the BizTalk Server Configuration wizard. Click the BizTalk EDI/AS2 Runtime node, and check the "Enable BizTalk EDI/AS2 Runtime Status Reporting for this BizTalk Group" property. You must configure BAM in order to configure EDI/AS2 status reporting.  
  
2.  In the BizTalk Server Administration Console, enable EDI status reporting for the party by clicking the "Activate EDI reporting" property in the General page of the EDI Properties dialog box. Enable AS2 status reporting for the party by clicking the "Activate AS2 reporting" property in the General page of the AS2 Properties dialog box. You must restart the BizTalk service after enabling EDI or AS2 status reporting.