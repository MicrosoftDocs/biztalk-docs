---
title: "How to Recover the BizTalk Server Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1d39e50-4296-49c7-bd1e-63b1325af168
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Recover the BizTalk Server Configuration
As part of recovering your BizTalk server, you must also import the configuration file that you created when you installed BizTalk Server.  
  
## Prerequisites  
 You must be logged on as a member of the Administrators group to perform this procedure.  
  
### To recover the BizTalk Server configuration  
  
1. Using Notepad, edit the BizTalk Server configuration file that you previously backed up, and enter the user account passwords for all of the BizTalk Server services.  
  
2. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
3. In **Microsoft BizTalk Server Configuration**, click **Import Configuration**.  
  
    Verify that there are no invalidation icons appearing in front of any feature. If any of the features have configuration errors, now is the time to correct them.  
  
4. Click **Apply Configuration**.  
  
    After all of the BizTalk Server features are configured, close the configuration window.  
  
## See Also  
 [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)   
 [How to Back Up The BizTalk Server Configuration](../core/how-to-back-up-the-biztalk-server-configuration.md)