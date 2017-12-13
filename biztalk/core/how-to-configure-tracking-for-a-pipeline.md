---
title: "How to Configure Tracking for a Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [pipelines], tracking warning"
  - "tracking, pipelines"
  - "tracking, warnings"
  - "configuring, pipelines"
  - "pipelines, tracking"
  - "managing [pipelines], configuring"
  - "tracking, configuring"
  - "pipelines, configuring"
  - "configuring [HAT tracking], pipelines"
  - "HAT, pipelines"
  - "managing [pipelines], tracking"
ms.assetid: 4f7f3c4a-4464-4170-a580-b4ce9296a097
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Tracking for a Pipeline
This topic describes how to use the BizTalk Server Administration to configure tracking for a pipeline. You might want to configure tracking for troubleshooting and auditing purposes. You can view message properties, port events, and message events. You can also track message events and port events for messages.  
  
 You can configure tracking for one of the default pipelines included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a custom pipeline that has been deployed into a BizTalk application. The tracking settings that you configure apply to all of the instances of the pipeline.  
  
> [!IMPORTANT]
>  Although you can configure tracking for a pipeline, this will generate a large amount of data because data is gathered globally for all ports that use the pipeline. We recommend instead that you configure tracking on your send and receive ports, as described in [How to Configure Tracking for a Send Port](../core/how-to-configure-tracking-for-a-send-port.md) and [How to Configure Tracking for a Receive Port](../core/how-to-configure-tracking-for-a-receive-port.md).  
  
 For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure tracking for a pipeline  
  
1.  Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Server Administration** and expand the BizTalk group containing the pipeline for which to configure tracking.  
  
3.  Do one of the following:  
  
    -   To configure tracking for one of the default BizTalk pipelines, expand \<All Artifacts\>.  
  
    -   To configure tracking for a custom pipeline that has been deployed into a BizTalk application, expand the application containing the pipeline.  
  
4.  Click the **Pipelines** folder, right-click the pipeline, and then click **Tracking**.  
  
    > [!NOTE]
    >  To configure tracking for multiple pipelines at once, hold down the Shift key, click each pipeline to configure, right-click one of the pipelines, and then click **Tracking**.  
  
5.  Configure tracking options you want, as described in the following table, and then click **OK**.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Track Events - Port start and end events**|Select this check box to track only when an instance starts and ends. Details include item name, assembly, and other metadata.|  
    |**Track Events - Message send and receive events**|Select this check box to track message send and receive events. This check box is available only if **Port start and end events** is selected.|  
    |**Track Message Bodies - Messages before pipeline processing**|Select this check box to save and track the message bodies received by the pipeline, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the raw message as submitted to the pipeline by the transport component. Depending on the application, the message might be encrypted, signed, or encoded. When using a BizTalk map, if this is a receive pipeline, tracking takes place after the inbound map is processed.<br /><br /> This check box is available only if **Message send and receive events** is selected.|  
    |**Track Message Bodies - Messages after pipeline processing**|Select this check box to save and track the message bodies sent by the pipeline, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the processed message to be submitted to the MessageBox database, which may be XML depending on your application. When using a BizTalk map, if this is a send pipeline, tracking takes place before the outbound map is processed.<br /><br /> This check box is available only if **Message send and receive events** is selected.|  
  
## See Also  
 [Managing Pipelines](../core/managing-pipelines.md)
