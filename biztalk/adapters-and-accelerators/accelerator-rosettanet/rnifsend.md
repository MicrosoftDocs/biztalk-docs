---
description: "Learn more about: RNIFSend"
title: "RNIFSend"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# RNIFSend
This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend.aspx file that prepares a message for RNIF processing, and sends the message to the RNIFReceive.aspx page at the responder. You can customize the ASPX page to do the following:  
  
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
