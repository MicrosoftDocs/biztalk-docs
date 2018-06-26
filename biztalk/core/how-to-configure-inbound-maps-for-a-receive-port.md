---
title: "How to Configure Inbound Maps for a Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [receive ports], configuring"
  - "configuring, maps"
  - "configuring, inbound maps"
  - "maps, configuring"
  - "receive ports, configuring"
  - "receive ports, inbound maps"
  - "configuring, receive ports"
  - "maps, inbound"
  - "managing [receive ports], inbound maps"
ms.assetid: b7448b39-f024-4353-818b-f753c2d60751
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Inbound Maps for a Receive Port
This topic describes how to use the BizTalk Server Administration console to configure inbound maps for a receive port. You use inbound maps to transform inbound messages from one schema to another; for example to transform messages received from a partner into a schema that your company uses.  
  
 You use a map to apply an XSL transformation to a message sent by the receive port without processing the message through an orchestration. You can add an inbound map, remove a map, or change an existing map to a different one. You can add more than one map to a receive port, but each map must have a unique source schema. For background information about maps, see [Maps](../core/maps.md).  
  
> [!NOTE]
>  The application developer can configure maps for a receive port during the development process by using the procedure in this.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure inbound maps for a receive port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure an inbound maps for a receive port.  
  
3. Click **Receive Ports**, right-click the receive port, click **Properties**, and then click **Inbound Maps**.  
  
4. Configure the inbound maps as described in the following table, and then click **OK**.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Remove**|Click to remove the selected map.|  
   |**Source Document**|From the drop-down list, select the source schema to use with this port.|  
   |**Map**|From the drop-down list, select the map you want to associate with this port.|  
   |**Target Document**|From the drop-down list, select the destination schema to use with this port.|  
  
## See Also  
 [Managing Receive Ports](../core/managing-receive-ports.md)   
 [Managing Maps](../core/managing-maps.md)