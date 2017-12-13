---
title: "Enable tracking on a Send Port | Microsoft Docs"
description: Turn on message body tracking and track message properties on a send port in BizTalk Server
ms.custom: ""
ms.date: "12/13/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure Tracking for a Send Port
Use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a send port, such as options to view message bodies and promoted properties. This helps you monitor the health of your BizTalk implementation and identify any bottlenecks. The tracking settings that you configure apply to all of the instances of the send port.  
  
 For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Enable tracking on a send port  
  
1.  In **BizTalk Server Administration**, expand the BizTalk group, and then expand your BizTalk application that has the send port.  
  
2.  Select **Send Ports**, right-click the send port, select **Properties**, and then select **Tracking**.  
  
    > [!NOTE]
    >  One send port can be associated with only one send pipeline. If message body tracking is disabled on the send pipeline, then nothing is tracked on the send port. In such a scenario, you can disable the "Tracking" options on that send port.  
  
3.  Use the following details to enable the tracking options you want, and then select **OK** to save your changes.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Track Message Bodies - Request message before port processing**|Saves and tracks message content before the message is received. <br/><br/> **Note**: Be sure to enable message body pipeline tracking to successfully track the response message before port processing.|  
    |**Track Message Bodies - Request message after port processing**|Saves and tracks message content after the message is received.|  
    |**Track Message Bodies – Response message before port processing**|Saves and tracks message content before the message is sent. Only available for solicit-response send ports.|    
    |**Track Message Bodies – Response message after port processing**|Saves and tracks message content after the message is sent. Only available for solicit-response send ports.|  
    |||
    |**Track Message Bodies – Response message after port processing**|Tracks the promoted properties of an inbound message.|  
    |**Track Message Properties - Request message after port processing**|Tracks the promoted properties of an outbound message.|  
    |**Track Message Properties – Response message before port processing**|Saves and tracks message properties before the message is sent. Only available for solicit-response send ports.|   
    |**Track Message Properties – Response message after port processing**|Saves and tracks properties after the message is sent. Only available for solicit-response send ports.|   
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)
