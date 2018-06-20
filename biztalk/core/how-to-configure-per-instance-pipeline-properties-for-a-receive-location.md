---
title: "How to Configure Per-instance Pipeline Properties for a Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, properties"
  - "receive locations, configuring"
  - "managing [pipelines], properties"
  - "managing [pipelines], receive locations"
  - "managing [receive locations], pipelines"
  - "managing [pipelines], configuring"
  - "pipelines, receive locations"
  - "pipelines, configuring"
  - "receive locations, pipelines"
  - "managing [receive locations], configuring"
ms.assetid: e1ed3b10-2f39-479b-a3e6-22b4b2872192
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Per-instance Pipeline Properties for a Receive Location
This topic describes how to use the BizTalk Server Administration console to configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group. Changes that you make overwrite the default pipeline properties for this receive location only, so if you want, you can configure different pipeline properties for each receive location in the BizTalk group.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
> [!NOTE]
>  When using per-instance pipeline properties to set the value for the **DocumentSpecNames** property in the XML disassembler component of a pipeline, the specified document schema and the pipeline must be defined in the same project.  
  
### To configure per-instance pipeline properties for a receive location  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the receive location for which to configure pipeline properties, expand **Applications**, and then expand the application containing the receive location.  
  
3. Click the **Receive Locations** folder, right-click the receive location, and then click **Properties**.  
  
4. Click the ellipsis (…) to the right of the **Receive Pipeline** box.  
  
5. Configure the properties you want, and then click **OK**. For more information, click **Help** on the properties page.  
  
   > [!IMPORTANT]
   >  Make sure that you enter correct information for pipelines properties. If you enter an invalid value, for example a string rather than a number, it will generate an error.  
  
6. If this is a request-response receive location, click the ellipsis (…) to the right of the **Send Pipeline** box.  
  
7. Configure the properties you want, and then click **OK** twice. For more information, click **Help** on the properties page.  
  
## See Also  
 [Managing Pipelines](../core/managing-pipelines.md)   
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)   
 [Managing Receive Locations](../core/managing-receive-locations.md)