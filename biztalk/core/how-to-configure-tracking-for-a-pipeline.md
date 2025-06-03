---
title: "Enable pipeline tracking"
description: Track message bodies and events when the pipeline processes messages in BizTalk Server
ms.custom: ""
ms.date: "12/13/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Configure pipeline tracking in BizTalk Server
Use the BizTalk Server Administration to configure tracking for a pipeline. You might want to configure tracking for troubleshooting and auditing purposes. You can view message properties, port events, and message events. You can also track message events and port events for messages.  
  
 You can configure tracking for one of the default pipelines included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a custom pipeline that has been deployed into a BizTalk application. The tracking settings that you configure apply to all of the instances of the pipeline.  
  
> [!IMPORTANT]
>  Although you can configure tracking for a pipeline, this generates a large amount of data because data is gathered globally for all ports that use the pipeline. Instead, we recommend that you configure tracking on your send and receive ports, as described in [Configure Tracking for a Send Port](../core/how-to-configure-tracking-for-a-send-port.md) and [Configure Tracking for a Receive Port](../core/how-to-configure-tracking-for-a-receive-port.md).  
  
 For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)  
  
## Prerequisites  
Sign in with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Enable pipeline tracking
  
1.  In **BizTalk Server Administration**, expand the BizTalk group that contains the pipeline. 
  
2.  Do one of the following:  
  
    -   To configure tracking for one of the default BizTalk pipelines, expand \<All Artifacts\>.  
  
    -   To configure tracking for a custom pipeline that has been deployed into a BizTalk application, expand the application containing the pipeline.  
  
3.  Select the **Pipelines** folder, right-click the pipeline, and then select **Tracking**.  
  
    > [!NOTE]
    >  To configure tracking for multiple pipelines at once, hold down the Shift key, select each pipeline to configure, right-click one of the pipelines, and then select **Tracking**.  
  
4.  Use the follwoing details to configure the tracking options you want, and then select **OK** to save your changes.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Track Events - Port start and end events**|Tracks only when an instance starts and ends. Details include item name, assembly, and other metadata.|  
    |**Track Events - Message send and receive events**|Tracks message send and receive events. Only available if **Port start and end events** is selected.|  
    |**Track Message Bodies - Messages before pipeline processing**|Saves and tracks the message bodies received by the pipeline, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the raw message as submitted to the pipeline by the transport component. Depending on the application, the message might be encrypted, signed, or encoded. When using a BizTalk map, if this is a receive pipeline, tracking takes place after the inbound map is processed.<br /><br /> Only available if **Message send and receive events** is selected.|  
    |**Track Message Bodies - Messages after pipeline processing**|Saves and tracks the message bodies sent by the pipeline, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the processed message to be submitted to the MessageBox database, which may be XML depending on your application. When using a BizTalk map, if this is a send pipeline, tracking takes place before the outbound map is processed.<br /><br /> Only available if **Message send and receive events** is selected.|  
  
## See Also  
 [Managing Pipelines](../core/managing-pipelines.md)
