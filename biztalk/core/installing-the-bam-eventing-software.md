---
title: "Installing the BAM-Eventing Software | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3638d34-f5a8-4ffd-99eb-d38aed4c0732
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing the BAM-Eventing Software
To implement BAM solutions using the BAM eventing APIs or configure your Windows Workflow Foundation or Windows Communication Foundation application to use the BAM interceptor for Windows Workflow Foundation, you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program. This software can be installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime or separately by selecting BAM Eventing Support under Additional Software in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup application.  
  
### To install the BAM-Eventing software  
  
1. Log on to the computer that will host the WF application using an account that has Administrator privileges.  
  
2. Run the Setup program on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Installation CD.  
  
3. Clear all selected options. If you do not perform this step, you may install software you do not need.  
  
4. Expand **Additional Software**, and then select the **BAM-Eventing** check box.  
  
5. Click **Next**.  
  
6. Click **Install**.  
  
7. When the installation procedure is complete, click **OK**.  
  
    The BAM-Eventing software is now installed.  
  
> [!NOTE]
>  Installing the BAM interceptor library using this method does not require the purchase of additional licenses.  
  
 If you are interested in monitoring performance counter data for the BAM interceptors, you must first register them by using InstallUtil.exe.  
  
### To register BAM interceptor performance counters by using InstallUtil.exe  
  
1. Start **[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt** as an administrator.  
  
2. At the command prompt, enter the following command:  
  
    InstallUtil [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\Microsoft.BizTalk.Bam.Interceptors.dll  
  
3. Type **Exit**, and then press ENTER to close the command prompt.  
  
    The BAM interceptor performance counters are now available.  
  
> [!NOTE]
>  By default, only Administrators and some system accounts have permission to log performance data. To enable access on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], add the account used for running workflow applications to the Performance Log Users group.  
  
## See Also  
 [Implementing BAM Solutions](../core/implementing-bam-solutions.md)   
 [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)