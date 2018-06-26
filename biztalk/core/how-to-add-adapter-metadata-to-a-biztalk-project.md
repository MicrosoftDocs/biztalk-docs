---
title: "How to Add Adapter Metadata to a BizTalk Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e439e5bf-94b3-4582-bacc-b058e6eb8e17
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Adapter Metadata to a BizTalk Project
The Add Adapter Metadata Wizard enables you to add adapter metadata to a BizTalk project. This data includes schemas, message types, and port types needed to communicate with an adapter from an orchestration. Use the Add Adapter Metadata Wizard with application adapters, such as FTP, to pull schemas corresponding to these application adapters into the system. Note that transport adapters such as HTTP do not typically use schemas.  
  
 The following procedure walks you through the generic steps to add metadata for an adapter.  
  
### To add adapter metadata to a BizTalk project  
  
1. In your [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, in Solution Explorer, right-click your project, click **Add**, and then click **Add Generated Items**.  
  
2. In the **Add Generated Items - \<**<em>Project name</em>**\>** dialog box, in the **Templates** section, select **Add Adapter**, and then click **Open**.  
  
3. In the Add Adapter Metadata Wizard, on the **Select Adapter** page, do the following.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |Adapter list box|Select the registered adapter to add to the project.|  
   |SQL Server|Enter the BizTalk database server name.|  
   |Database|Displays the list of BizTalk Management databases for the chosen server.|  
   |Port|Optional. Displays the list of ports created and stored in the BizTalk Management database. Only ports configured to work with the selected adapter are shown.|  
  
    Click **Next**.  
  
   > [!NOTE]
   >  Attempting to add generated schemas that contain characters that the **System.XML.XMLConvert** class does not support results in a compilation error.  
  
4. If you are using a static adapter, on the **Select Services to Import** page, select a set of available services from the tree view, and then click **Finish**.  
  
    –Or–  
  
    If you are using a dynamic adapter, follow the steps in the custom user interface to complete the wizard.  
  
   After you complete the wizard, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] lists the .odx and .xsd files in Solution Explorer.