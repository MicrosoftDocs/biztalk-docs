---
title: "How to Start TI Manager1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e65d569-2312-4a0d-84af-8b2205bd51bf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Start TI Manager
You can start TI (Transaction Integrator) Manager many different ways:  
  
- Use the **Start** menu  
  
- Start Microsoft Management Console (MMC), and then add the appropriate snap-in consoles  
  
- Double-click a saved MMC configuration file (.msc file)  
  
- Enter a command line at a command prompt  
  
- Use the **Run** command on the **Start** menu  
  
  You can also start TI Manager from MMC. Then you can save your MMC configuration as an .msc file, so that later you can just double-click the .msc file to start it. This technique can be useful when you are adding other snap-ins to MMC in addition to the TI Manager snap-ins.  
  
### To start TI Manager from the Start menu  
  
-   Click **Start**, point to **Programs**, point to **Host Integration Server**, point to **Application Integration**, and then click **TI Manager**.  
  
### To start TI Manager from MMC  
  
1.  Start MMC by doing one of the following:  
  
    1.  Click **Start**, click **Run**, type `mmc`, and then click **OK**.  
  
    2.  Type `mmc` at a command prompt, and then press ENTER.  
  
2.  On the **Console** menu, click **Add/Remove Snap-in**.  
  
3.  In the **Add/Remove Snap-in** dialog box, click **Add**.  
  
4.  In the **Add Standalone Snap-in** dialog box, double-click **TI Manager**.  
  
5.  In the **Specify machine to administer** dialog box, click **Local computer**.  
  
6.  Click **Finish**.  
  
7.  In the **Add Standalone Snap-in** dialog box, double-click **Component Services** (or **Microsoft Transaction Server**).  
  
8.  In the **Add Standalone Snap-in** dialog box, click **Close**.  
  
9. In the **Add/Remove Snap-in** dialog box, click **OK**.  
  
     If you save the configuration as, for example, MyCOMTI.msc, you can run it again later by double-clicking the file name.  
  
### To start TI Manager from the command  
  
1.  Click **Start**, and then click **Run**.  
  
2.  Type the following:  
  
     `MMC "c:\Program Files\Host Integration Server\System\ComtiComPlus.msc"`  
  
3.  Click **OK**.  
  
     Make sure that you include the quotation marks because the path contains spaces.  
  
## Starting TI Manager from the Command Line  
 You can also start TI Manager from a command line. Include the path and file name of the .msc file when you use the **Run** command or from a command prompt. Microsoft has included two .msc files (ComtiComPlus.msc and ComtiMTS.msc) for you in the Host Integration Server\System folder. The following procedure is an example.  
  
 If you previously added TI Manager to a remote computer, you can use the command line to start TI Manager for the remote computer if you know the name of that computer. However, you must have enabled the following option at the time that you added the console for the remote computer: Allow the selected computer to be changed when launching from the command line. For example, if you created a file named MyOtherCOMTI.msc on another computer in a Windows network, you can run it on your local computer by using the following procedure.  
  
#### To start a remote TI Manager from the command line  
  
1.  Click **Start**, and then click **Run**.  
  
2.  Type the following:  
  
     `MMC "C:\Program Files\Host Integration Server\System\MyOtherCOMTI.msc" /computer=computername`  
  
3.  Click **OK**.  
  
     Adding the **/computer=computername** option lets you configure and otherwise manage all your TI environments from a single computer.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)   
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)