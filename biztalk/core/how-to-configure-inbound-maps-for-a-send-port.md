---
title: "How to Configure Inbound Maps for a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [send ports], inbound maps"
  - "configuring, send ports"
  - "send ports, inbound maps"
  - "configuring, inbound maps"
  - "managing [send ports], configuring"
  - "send ports, configuring"
ms.assetid: 213c66ba-928f-4c00-9a87-f45eaa9f7dca
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Inbound Maps for a Send Port
This topic describes how to use the BizTalk Server Administration console to configure inbound maps for a send port. Inbound maps are used only with dynamic or static solicit-response send ports. You use a map to apply an XSL transformation to a response message received by the port without processing the message through an orchestration. You can add an inbound map, remove a map, or change an existing map to a different one. You can add more than one map to a send port, but each map must have a unique source schema. For background information about maps, see [Maps](../core/maps.md).  
  
> [!NOTE]
>  The application developer can configure maps during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure inbound maps for a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure an inbound map for a send port.  
  
3. Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Inbound Maps**.  
  
4. Configure the inbound maps as described in the following table, and then click **OK**. Repeat as needed to add or remove multiple maps.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Remove**|Click to remove the selected map.|  
   |**Source Document**|From the drop-down list, select the source document for the inbound map.|  
   |**Map**|From the drop-down list, select the map to associate with the source and target documents.|  
   |**Target Document**|From the drop-down list, select the target document for the inbound map.|  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)   
 [Managing Maps](../core/managing-maps.md)