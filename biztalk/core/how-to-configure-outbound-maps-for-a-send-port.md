---
title: "How to Configure Outbound Maps for a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, outbound maps"
  - "configuring, send ports"
  - "managing [send ports], configuring"
  - "send ports, outbound maps"
  - "send ports, configuring"
  - "managing [send ports], outbound maps"
ms.assetid: 9f5f5504-5a7f-4b21-9a65-91dce9d35890
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Outbound Maps for a Send Port
This topic describes how to configure outbound maps for a send port by using the BizTalk Server Administration console. You use a map to apply an XSL transformation to a message sent by the send port without processing the message through an orchestration. You can add an outbound map, remove a map, or change an existing map to a different one. You can add more than one map to a send port, but each map must have a unique source schema. For background information about maps, see [Maps](../core/maps.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure outbound maps for a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure the outbound maps for a send port.  
  
3. Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Outbound Maps**.  
  
4. Configure outbound maps as described in the following table, and then click **OK**. Repeat as needed to add or remove multiple maps.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Remove**|Click to remove the selected map.|  
   |**Outbound maps - Source Document**|From the drop-down list, select the source document for the outbound map.|  
   |**Outbound maps - Map**|From the drop-down list, select the map to associate with the source and target documents.|  
   |**Outbound maps - Target Document**|From the drop-down list, select the target document for the outbound map.|  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)   
 [Managing Maps](../core/managing-maps.md)