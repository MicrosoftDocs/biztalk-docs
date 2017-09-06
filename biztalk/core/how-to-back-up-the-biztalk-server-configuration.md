---
title: "How to Back Up The BizTalk Server Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14f89050-c204-4d44-a875-299e690489ef
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Back Up The BizTalk Server Configuration
As part of backing up [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you should back up the configuration settings associated with the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Having a copy of the original configuration file greatly simplifies the restoration process if you have a hardware failure that requires you to replace the computer.  
  
 The configuration settings for each computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are stored in an XML file created by the BizTalk Server Configuration Manager. Any time you change the configuration of your BizTalk servers, you should export the updated configuration file to your backup location. This helps to ensure that the configuration file is available if you have to replace your BizTalk server.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.  
  
### To back up the BizTalk Server configuration  
  
1.  Click **Start**, click **All Programs**, click **Microsoft BizTalk Server**, and then click **BizTalk Server Configuration**.  
  
2.  In **Microsoft BizTalk Server Configuration**, click **Export Configuration**.  
  
3.  In the **Save As** dialog box, browse to the location where you store your backups.  
  
4.  In the **File name** box, type a name for the configuration file, and then click **Save**.  
  
## See Also  
 [Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)   
 [How to Recover the BizTalk Server Configuration](../core/how-to-recover-the-biztalk-server-configuration.md)