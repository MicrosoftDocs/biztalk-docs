---
title: "How to Disable Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b1e6cdd-8266-494d-b6e7-260ac5a4f2fb
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Disable Tracking
This topic describes how to disable tracking using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can configure various tracking options during runtime for orchestrations, send ports, receive ports, and pipelines using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can change the tracking options for an item at any time, without interrupting the business process.  

## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information about permissions, see [Permissions for Managing an Application](../technical-guides/permissions-for-managing-an-application.md).  

> [!NOTE]
>  If you only want to view the tracking options, you can be logged on as a member of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group.  

##  <a name="BKMK_DisableOrchTracking"></a> To disable tracking for an orchestration  

1. Click **Start**, click **All Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to configure tracking.  

3. Click **Orchestrations**, and from the right pane, right-click the orchestration for which you want to configure tracking, and then click **Properties**.  

4. Click the **Tracking** tab, disable tracking options as described in the following table, and then click **OK**.  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Track Events - Orchestration start and end**|Clear this check box to disable tracking of the orchestration instance before and after processing of the entire business process.|  
   |**Track Events - Message send and receive**|Clear this check box to disable tracking of message send and receive events. This check box is available only if you select the **Orchestration start and end** check box.|  
   |**Track Events - Shape start and end**|Clear this check box when you do not need to debug orchestration instances in the Orchestration Debugger. When this check box is selected, the event list in the Orchestration Debugger is populated. This check box is available only if you select the **Orchestration start and end** check box.|  
   |**Track Message Bodies - Before orchestration processing**|Clear this check box to disable the saving and tracking of the actual message content prior to processing by the orchestration instance. This check box is available only if you select the **Message send and receive** check box.|  
   |**Track Message Bodies - After orchestration processing**|Clear this check box to disable the saving and tracking of the actual message content after processing by the orchestration instance. This check box is available only if you select the **Message send and receive** check box.|  
   |**Track Message Properties - Incoming messages**|Clear this check box to disable tracking of the promoted properties of an inbound message. This check box is available only if you select the **Message send and receive** check box.|  
   |**Track Message Properties - Outgoing messages**|Clear this check box to disable tracking of the promoted properties of an outbound message.  This check box is available only if you select the **Message send and receive** check box.|  

### To disable tracking for a send port  

1. Click **Start**, click **All Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port for which you want to configure tracking.  

3. Click **Send Ports**, right-click the send port, click **Properties**, and then click **Tracking**.  

4. Disable tracking options as described in the following table, and then click **OK**.  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Track Message Bodies - Request message before port processing**|Clear this check box to disable saving and tracking of message content before the message is received. **Note:**  You must enable message body pipeline tracking to successfully track the response message before port processing.|  
   |**Track Message Bodies - Request message after port processing**|Clear this check box to disable saving and tracking of message content after the message is received.|  
   |**Track Message Bodies - Response message before port processing**|Clear this check box to disable saving and tracking of message content before the message is sent. This check box is available only for solicit-response send ports.|  
   |**Track Message Bodies - Response message after port processing**|Clear this check box to disable saving and tracking of message content after the message is sent. This check box is available only for solicit-response send ports.|  
   |**Track Message Properties - Request message before port processing**|Clear this check box to disable tracking of the promoted properties of an inbound message.|  
   |**Track Message Properties - Request message after port processing**|Clear this check box if you do not want to track the promoted properties of an outbound message.|  
   |**Track Message Properties - Response message before port processing**|Clear this check box to disable saving and tracking of message properties before the message is sent. This check box is available only for solicit-response send ports.|  
   |**Track Message Properties - Response message after port processing**|Clear this check box to disable the saving and tracking of properties after the message is sent. This check box is available only for solicit-response send ports.|  

### To disable tracking for a receive port  

1. Click **Start**, click **All Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the receive port for which you want to configure tracking.  

3. Click **Receive Ports**, right-click the receive port, and then click **Tracking**.  

4. Disable tracking options as described in the following table, and then click **OK**.  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Track Message Bodies - Request message before port processing**|Clear this check box to disable saving and tracking of message content before the message is received.|  
   |**Track Message Bodies - Request message after port processing**|Clear this check box to disable saving and tracking of message content after the message is received.|  
   |**Track Message Bodies - Response message before port processing**|Clear this check box to disable saving and tracking of message content before the message is sent. This check box is available only for request-response receive ports. **Note:**  You must enable message body pipeline tracking to successfully track the response message before port processing.|  
   |**Track Message Bodies - Response message after port processing**|Clear this check box to disable saving and tracking of message content after the message is sent. This check box is available only for request-response receive ports.|  
   |**Track Message Properties - Request message before port processing**|Clear this check box to disable tracking of the promoted properties of an inbound message.|  
   |**Track Message Properties - Request message after port processing**|Clear this check box if you do not want to track the promoted properties of an outbound message.|  
   |**Track Message Properties - Response message before port processing**|Clear this check box to disable saving and tracking of message properties before the message is sent. This check box is available only for request-response receive ports.|  
   |**Track Message Properties - Response message after port processing**|Clear this check box to disable the saving and tracking of properties after the message is sent. This check box is available only for request-response receive ports.|  

### To disable tracking for a policy  

1. Click **Start**, click **Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the policy for which you want to configure tracking.  

3. Click **Policies**, right-click the policy, click **Properties**, and then click **Tracking**.  

4. Disable tracking options as described in the following table, and then click **OK**.  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Fast activity**|Clear this check box to disable tracking of the instance data on which the policy operates.|  
   |**Condition evaluation**|Clear this check box to disable tracking of the true/false results of conditions in the selected policy.|  
   |**Rule firings**|Clear this check box to disable tracking of the actions started as a result of the policy.|  
   |**Agenda updates**|Clear this check box to disable tracking of updates to the agenda. The agenda contains a list of actions that are "true" and need to fire.|  

### To disable tracking for a schema  

1. Click **Start**, click **Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the schema for which you want to configure tracking.  

3. Click **Schemas**, right-click the schema, and then click **Properties**.  

4. In the left pane, click **Tracking**.  

5. Do one of the following to specify which properties that you want to disable for tracking messages, and then click **OK**:  

   -   Clear the **Always track all properties** check box if you do not want to use all message properties regardless of the schema version. This check box is available only for document schemas.  

   -   Clear the **Select all message properties** check box if you do not want to use all the listed properties.  

   -   Under **Properties list**, clear the check box of each property that you do not want to use.  

   > [!NOTE]  
   >  You should select only the options that you need, because tracking messages creates performance and storage overhead for your system.  

### To disable tracking for a pipeline  

1. Click **Start**, click **Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

   > [!NOTE]  
   >  If you set tracking options on pipelines, you will also set the tracking options globally for every port that uses the pipeline. This, in turn, may result in far more data being tracked than you intended, which will slow system performance. Instead, you can set tracking options on send ports and receive ports.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the pipeline for which you want to configure tracking.  

3. Do one of the following:  

   -   To disable tracking for one of the default BizTalk pipelines, expand \<All Artifacts\>.  

   -   To disable tracking for a custom pipeline that has been deployed into a BizTalk application, expand the application containing the pipeline.  

4. Click the **Pipelines** folder, right-click the pipeline, and then click **Tracking**.  

   > [!NOTE]  
   >  To disable tracking for multiple pipelines at once, hold down the Shift key, click each pipeline to configure, right-click one of the pipelines, and then click **Tracking**.  

5. Disable tracking options as described in the following table, and then click **OK**.  


   |                Use this                |                                                                                                                                                                                                                                                                                                                                 To do this                                                                                                                                                                                                                                                                                                                                 |
   |----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |     **Port start and end events**      |                                                                                                                                                                                                                                                                  Clear this check box to disable tracking only when an instance starts and ends. Details include item name, assembly, and other metadata.                                                                                                                                                                                                                                                                  |
   |  **Message send and receive events**   |                                                                                                                                                                                                                                                      Clear this check box to disable the tracking of message send and receive events. This check box is available only if **Port start and end events** is selected.                                                                                                                                                                                                                                                       |
   | **Message before pipeline processing** | Clear this check box to disable saving and tracking of the message bodies received by the pipeline, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the raw message as submitted to the pipeline by the transport component. Depending on the application, the message might be encrypted, signed, or encoded. When using a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] map, if this is a receive pipeline, tracking takes place after the inbound map is processed.<br /><br /> This check box is available only if **Message send and receive events** is selected. |
   | **Message after pipeline processing**  |                        Clear this check box to disable saving and tracking of the message bodies sent by the pipeline, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the processed message to be submitted to the MessageBox database, which may be XML depending on your application. When using a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] map, if this is a send pipeline, tracking takes place before the outbound map is processed.<br /><br /> This check box is available only if **Message send and receive events** is selected.                        |

## See Also  
 [Maintaining Performance](../technical-guides/maintaining-performance.md)