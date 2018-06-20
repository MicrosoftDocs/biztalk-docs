---
title: "RNIFSend | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 780f7446-56c5-40bf-95e2-25d0cff12f12
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RNIFSend
This sample provides a working [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend.aspx file that prepares a message for RNIF processing, and sends the message to the RNIFReceive.aspx page at the responder. You can customize the ASPX page to do the following:  
  
- Add or remove performance counters  
  
- Add functionality to the page, such as writing data to a database or customizing tracking functionality  
  
- Add validation to the page  
  
  This sample is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFSender.  
  
## Demonstrates  
 This sample demonstrates how to prepare outgoing messages for RNIF processing, including the following:  
  
-   Validating the data for the MIME header  
  
-   Adding a MIME header and MIME boundaries to the message  
  
-   Sending the message to the partner's RNIFReceive.aspx  
  
-   Processing a returned signal message  
  
## See Also  
 [Send and Receive ASPX Pages](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Web Application Samples](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)