---
title: "How to Recover the BizTalk Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1010e55-7e3d-4565-8604-ea652ea4da8c
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Recover the BizTalk Group
You must rejoin the BizTalk Server to an existing BizTalk group as part of the system recovery process.  
  
## Prerequisites  
 You must be logged on as a member of the Administrators group to perform this procedure.  
  
 If you are recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition, you must download a script that facilitates recovery of the server. Download [RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkID=195799).  
  
### To recover the BizTalk group (Standard Edition)  
  
1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  At the command prompt, type:  
  
     **RestoreConfig.vbe**  *\<SavedConfigXML\>*  
  
     Where *\<SavedConfigXML\>* is the full path and filename of the saved configuration file.  
  
     The above should exit without displaying any errors.  
  
    > [!NOTE]
    >  To recover [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition on a 64-bit computer, you must run **RestoreConfig.vbe** from the 32-bit command prompt so that it can update the 32-bit registry. To open the 32-bit command prompt, click **Start**, click **Run**, type **c:\windows\syswow64\cmd.exe**, and then click **OK**.  
  
    > [!NOTE]
    >  The name of the computer that failed is contained in the saved configuration file. The name of the computer that you are restoring onto must have that same name. You must run the script above on a computer with that name. You can, however, change the name of the computer that failed in the saved configuration file. If you do so, you can run the script above onto a computer with a different name.  
  
### To recover the BizTalk group (Developer Edition or Enterprise Edition)  
  
1.  Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
2.  In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], in the console tree, click **Group**.  
  
3.  In the details pane, select **Join an existing BizTalk Group**, and then specify the appropriate remote BizTalk Management (BizTalkMgmtDb) database.  
  
4.  Click **Apply Configuration**.  
  
5.  Click **File**, and then click **Exit**.  
  
## See Also  
 [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)