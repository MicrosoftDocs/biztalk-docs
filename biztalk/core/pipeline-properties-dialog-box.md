---
title: "Pipeline Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.pipeline.properties"
ms.assetid: 595e8ade-ce12-4bbb-b9b0-ebeea7bb14a6
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pipeline Properties Dialog Box
You can use the **Pipeline Properties** window to view information on all the pipelines that are deployed in the application, as well as default pipelines that are deployed in every BizTalk installation. You can also configure message tracking options for pipelines. Pipeline properties are configured in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. The **Description** box is an exception; you can edit it in the **Pipeline Properties** window.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Displays the full name of the pipeline.|  
|**Assembly**|Displays the fully qualified name (name, version, culture, public key token) of the assembly that contains the pipeline.|  
|**Type**|Indicates whether the pipeline is a send or receive pipeline.|  
|**Description**|Type any text that helps you distinguish this pipeline from others. The maximum number of characters allowed is 256.|  
  
## Tracking Tab  
 Pipelines and orchestrations use virtually the same tracking options. You can track promoted message properties from pipelines just as you can from orchestrations.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Track Events - Port start and end events**|Select this check box to track only when an instance starts and ends. Details included are item name, assembly, and other metadata.|  
|**Track Events - Message send and receive events**|Select this check box to track message send and receive events. This check box is available only if **Port start and end events** is selected.|  
|**Track Message Bodies - Messages before pipeline processing**|Select this check box to save and track the actual message content as received by the pipeline, along with the shortcut, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the raw message as submitted to the pipeline by the transport component. Depending on the application, the message might be encrypted, signed, or encoded. When using a BizTalk map, if this is a receive pipeline, tracking takes place after the inbound map is processed.<br /><br /> This check box is available only if **Message send and receive events** is selected.|  
|**Track Message Bodies - Messages after pipeline processing**|Select this check box to save and track the actual message content as sent by the pipeline, along with the shortcut, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the processed message to be submitted to the MessageBox database, which may be XML depending on your application. When using a BizTalk map, if this is a send pipeline, tracking takes place before the outbound map is processed.<br /><br /> This check box is available only if **Message send and receive events** is selected.|  
  
## See Also  
 [About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md)   
 [How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md)   
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)   
 [Receive Pipelines](../core/receive-pipelines.md)   
 [Send Pipelines](../core/send-pipelines.md)