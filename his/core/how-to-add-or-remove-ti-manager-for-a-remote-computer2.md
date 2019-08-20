---
title: "How to Add or Remove TI Manager for a Remote Computer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19625d15-884a-4f24-85d4-9f891b06846c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Add or Remove TI Manager for a Remote Computer
You can use TI (Transaction Integrator) Manager to administer remote environments (RE) on your local client computer if you installed [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Server on that computer. However, TI cannot reside on a computer that has [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Administrator Client or [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] End-User Client installed instead of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Server.  
  
 Once you install [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Server on the computer, you can use TI Manager to deploy TI components in COM+ applications on the local computer.  
  
 You can display a TI Manager on your local computer for your local computer and for up to nine remote computers that are currently running TI. This means that, from a single computer, you can administer the remote environment configurations on a maximum of 10 computers.  
  
### To add TI Manager consoles for remote computers to your local computer  
  
1.  Open Microsoft Management Console (MMC) by doing one of the following:  
  
    1.  Click **Start**, click **Run**, type `mmc`, and then click **OK**.  
  
    2.  Type `mmc` at a command prompt, and then press ENTER.  
  
2.  On the **Console** menu, click **Add/Remove Snap-in**.  
  
3.  In the **Add/Remove Snap-in** dialog box, click **Add**.  
  
4.  In the **Add Standalone Snap-in** dialog box, double-click **TI Manager**.  
  
5.  In the **Specify computer to administer** dialog box, click **Another Computer** and type the name of that computer (for example, mycomputer2).  
  
6.  If needed, select the **Allow the selected computer** check box so that in the future, you can specify a different computer when you start TI Manager from the command line. To learn how to do this, see [How to Start TI Manager](../core/how-to-start-ti-manager1.md).  
  
7.  Click **Finish**.  
  
8.  Repeat steps 4–7 for each remote computer that you want to administer from your local computer. You can add a maximum of nine.  
  
9. In the **Add Standalone Snap-in** dialog box, click **Close**.  
  
10. In the **Add/Remove Snap-in** dialog box, click **OK**.  
  
### To remove a TI Manager console  
  
1.  On the TI Manager master menu, click **Console**.  
  
2.  Click **Add/Remove Snap-in**.  
  
3.  Click the TI console that you want to remove, click **Remove**, and then click **OK**.  
  
## See Also  
 [Managing Transaction Integrator with TI Manager](../core/managing-transaction-integrator-with-ti-manager2.md)   
 [Getting Started with TI](../core/getting-started-with-ti1.md)