---
title: "How to Configure Per-Instance Pipeline Properties for a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, properties"
  - "managing [pipelines], properties"
  - "configuring, send ports"
  - "configuring, pipelines"
  - "managing [pipelines], configuring"
  - "managing [send ports], pipelines"
  - "managing [send ports], configuring"
  - "send ports, pipelines"
  - "pipelines, configuring"
ms.assetid: c58faa9e-0dfb-458b-8f1b-d3c91bce0436
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Per-Instance Pipeline Properties for a Send Port
This topic describes how to use the BizTalk Server Administration console to configure pipeline properties for a send port after the pipeline has been deployed into a BizTalk group. Changes that you make overwrite the default pipeline properties for this send port only, so if you want, you can configure different pipeline properties for each send port in the BizTalk group.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
> [!NOTE]
>  When using per-instance pipeline properties to set the value for the **DocumentSpecNames** property in the XML disassembler component of a pipeline, the specified document schema and the pipeline must be defined in the same project.  
  
### To configure per-instance pipeline properties for a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the send port for which you want to configure pipeline properties, expand **Applications**, and then expand the application containing the send port.  
  
3. Click the **Send Ports** folder, right-click the send port, and then click **Properties**.  
  
4. Click the ellipsis (**…**) button to the right of the **Send Pipeline** box.  
  
5. Configure the properties you want, and then click **OK**. Click **Help** on the properties page for more information.  
  
   > [!IMPORTANT]
   >  Make sure that you enter correct information for pipelines properties. If you enter an invalid value, for example a string rather than a number, it will generate an error.  
  
6. If this is a solicit-response send port, click the ellipsis (**…**) button to the right of the **Receive Pipeline** box.  
  
7. Configure the properties you want, and then click **OK** twice. Click **Help** on the properties page for more information.  
  
## See Also  
 [Managing Pipelines](../core/managing-pipelines.md)   
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)   
 [Managing Receive Locations](../core/managing-receive-locations.md)