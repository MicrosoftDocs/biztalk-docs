---
title: "Orchestration Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.orchestration.properties"
ms.assetid: eb5af3a9-a9bd-4c11-a961-6a203f2a9d24
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestration Properties Dialog Box
Use the **Orchestration Properties** window to view and configure information about the orchestration you have selected in the details pane.  
  
## General Tab  
 The name and assembly information on the **General** tab are created when you create the orchestration in Microsoft Visual Studio. You can add information to the **Description** box at any time.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Displays the orchestration name and the .NET assembly that contains it.|  
|**Assembly**|Displays the fully qualified name (name, version, culture, public key token) of the assembly that contains the orchestration.|  
|**Description**|Type any text that will help you distinguish this orchestration from others. The maximum number of characters allowed is 256.|  
  
## Bindings Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host**|From the drop-down list, select the Host on which to enlist an orchestration.|  
|**Bindings**|From the drop-down lists under Receive Ports and Send Ports/Send Port Groups, select Send and Receive ports to bind to respective logical ports.|  
  
## Tracking Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Track Events - Orchestration start and end**|Select this check box to track the orchestration instance before and after processing of the entire business process. Orchestration tracking enables you to see the instances in the message event and service instance tracking queries from the Group Hub page.|  
|**Track Events - Message send and receive**|Select this check box to track message send and receive events. This check box is available only if you select the **Orchestration start and end** check box.|  
|**Track Events - Shape start and end**|Select this check box when you need to debug orchestration instances in the Orchestration Debugger. When this check box is selected, the event list in the Orchestration Debugger is populated. This check box is available only if you select the **Orchestration start and end** check box.|  
|**Track Message Bodies - Messages before orchestration processing**|Select this check box to save and track the actual message content prior to processing by the orchestration instance. This check box is available only if you select the **Message send and receive** check box.|  
|**Track Message Bodies - Messages after orchestration processing**|Select this check box to save and track the actual message content after processing by the orchestration instance. This check box is available only if you select the **Message send and receive** check box.|  
|**Track Message Properties - Incoming messages**|Select this check box to track the promoted properties of an inbound message.|  
|**Track Message Properties - Outgoing messages**|Select this check box to track the promoted properties of an outbound message.|  
  
## See Also  
 [Creating Orchestrations](../core/creating-orchestrations.md)   
 [About Orchestrations](../core/about-orchestrations.md)   
 [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md)