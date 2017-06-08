---
title: "Receive Port Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.receiveport.properties"
ms.assetid: ad315dc4-2894-4bcf-84d9-e2827b328f7c
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Port Properties Dialog Box
Use the **Receive Port Properties** window to view the properties of an existing receive port and to create and configure a new receive port.  
  
## General Tab  
 Specific properties that are applicable only to two-way ports are hidden for one-way ports.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Type the name of the port.|  
|**Port type**|Displays the port type. Receive ports may be one-way or request-response. You select the port type when you create the port; if an existing port is the wrong type for your purposes, you must re-create the port.|  
|**Authentication - No Authentication**|Click this option to disable authentication when party resolution authentication is configured.|  
|**Authentication - Drop messages if authentication fails**|Click this option to enable authentication, but drop unauthenticated messages. This option takes effect when party resolution authentication is configured.|  
|**Authentication - Keep messages if authentication fails**|Click this option to enable authentication and keep unauthenticated messages. Messages are kept in the suspended queue. This option takes effect when party resolution authentication is configured.|  
|**Enable routing for failed messages**|Select this check box to attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule). Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK). The default value is cleared.|  
|**Description**|Type any text that will help you distinguish this receive port from others. The maximum number of characters allowed is 256.|  
  
## Receive Locations Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**New**|Click to open the **Receive Location Properties** page and set up a new receive location.|  
|**Delete**|Click to delete the selected receive location.|  
|**Properties**|Click to open the **Receive Location Properties** window for the selected receive location.|  
|**Name**|Displays the name of a receive location.|  
|**URI**|Displays the adapter type and the receive location address.|  
  
## Inbound Maps Tab  
 You can use a map to apply an XSL transformation of an inbound message at the receive port without processing the message through an orchestration. You can add more than one map to a receive port, but each map must have a unique source schema.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Remove**|Click to remove the selected map.|  
|**Source Document**|From the drop-down list, select the source schema to use with this port.|  
|**Map**|From the drop-down list, select the map you want to associate with this port.|  
|**Target Document**|From the drop-down list, select the destination schema to use with this port.|  
  
## Outbound Maps Tab  
 You can use a map to apply an XSL transformation of a response message sent by the receive port without processing the message through an orchestration. You can add more than one map to a receive port, but each map must have a unique source schema.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Remove**|Click to remove the selected map.|  
|**Source Document**|From the drop-down list, select the source schema to use with this port.|  
|**Map**|From the drop-down list, select the map you want to associate with this port.|  
|**Target Document**|From the drop-down list, select the destination schema to use with this port.|  
  
## Tracking Tab  
 Message body tracking saves messages after service instances processing is complete. Message property tracking provides a record of promoted properties for each message in the Results list, and enables you to locate a specific message.  
  
> [!NOTE]
>  Specific properties that are applicable only to two-way ports are hidden for one-way ports.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Track Message Bodies - Request message before port processing**|Select this check box to enable you to save and track message content before the message is received.|  
|**Track Message Bodies - Request message after port processing**|Select this check box to enable you to save and track message content after the message is received.|  
|**Track Message Properties - Request message before port processing**|Select this check box to track the promoted properties of an inbound message.|  
|**Track Message Properties - Request message after port processing**|Select this check box if you want to track the promoted properties of an outbound message.|  
|**Track Message Bodies - Response message before port processing**|Select this check box to enable you to save and track message content before the message is sent.|  
|**Track Message Bodies - Response message after port processing**|Select this check box to enable you to save and track message content after the message is sent.|  
|**Track Message Properties - Response message before port processing**|Select this check box to track the promoted properties of an outbound message.|  
|**Track Message Properties - Response message after port processing**|Select this check box if you want to track the promoted properties of an inbound message.|  
  
## See Also  
 [How to Create a Receive Port](../core/how-to-create-a-receive-port.md)