---
description: "Learn more about: RNIFReceive"
title: "RNIFReceive"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# RNIFReceive
This sample provides a working Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFReceive.aspx file that receives an RNIF message, and prepares it for processing by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public process. You can customize the ASPX page to do the following:  
  
- Add or remove performance counters  
  
- Add functionality to the page, such as writing data to a database or customizing tracking functionality  
  
- Add validation to the page  
  
  This sample is located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\WebApplication\RNIFReceiver.  
  
## Demonstrates  
 This sample demonstrates how to prepare incoming messages for the public process, including the following:  
  
-   Receiving the message from the partner's RNIFSend.aspx  
  
-   Validating the MIME header  
  
-   Removing the MIME header and boundaries from the message  
  
-   Routing the message to the partner's RNIFReceive.aspx  
  
-   Returning a signal message  
  
## See Also  
 [Send and Receive ASPX Pages](../../adapters-and-accelerators/accelerator-rosettanet/send-and-receive-aspx-pages.md)   
 [Web Application Samples](../../adapters-and-accelerators/accelerator-rosettanet/web-application-samples.md)
