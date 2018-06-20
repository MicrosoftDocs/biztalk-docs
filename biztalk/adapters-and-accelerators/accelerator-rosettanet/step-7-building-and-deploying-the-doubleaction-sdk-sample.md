---
title: "Step 7: Building and Deploying the DoubleAction SDK Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "double action tutorial, building solutions"
  - "deploying, solutions"
  - "building solutions"
  - "double action tutorial, deploying solutions"
ms.assetid: f67f8aee-1004-48ee-a6fd-881097382888
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Building and Deploying the DoubleAction SDK Sample
The DoubleAction.odx sample shows how to implement an orchestration to generate responses automatically for the double-action Partner Interface Processes (PIPs) 0C2, 0C4, 3A2, and 3A4. You can extend this sample project to support additional double-action PIPs.  
  
 You use this sample to send a response automatically to Fabrikam whenever Fabrikam makes a request using any one of the four PIPs.  
  
### To build and initialize the DoubleAction sample  
  
1. On the Contoso computer, in a command prompt window, move to the following folder:   
   *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction\\.  
  
   > [!NOTE]
   >  Before running the Setup program, open the DoubleAction.sql file (in the above folder) in Notepad. On the **File** menu, click **Save As**. In the **Encoding** box, select **ANSI** from the drop-down list, and then click **Save**. Click **Yes** to overwrite the existing file.  
  
2. If your BizTalk Server installation is running on SQL Server 2008 R2/2008 SP1, run setupx64.bat in the same folder. The batch file will perform the following actions:  
  
   - Creates a SQL stored procedure (`PipAutomationGetAction`) in the BTARNDATA database to retrieve the action message from the MessagesToLOB table.  
  
   - Compiles the HeaderHelper .NET project and registers the assembly in the global assembly cache.  
  
   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SQL receive port (MessagesToLOB_Receive_Port).  
  
   - Enables the receive location (MessagesToLOB_Receive_Location).  
  
   - Compiles and deploys the double-action PIPAutomation orchestration (DoubleAction.odx).  
  
   - Binds and starts the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration.  
  
     > [!NOTE]
     >  The sample displays some warnings while compiling. You can ignore these warnings.  
  
     > [!NOTE]
     >  Verify that DoubleAction.odx has been bound to **MessagesToLOB_Receive_Port**, and that the orchestration has been started.  
  
3. In BizTalk Server Administration Console, expand the **BizTalk Group**, **Applications**, and **BizTalk Application 1** nodes. Click the **Orchestrations** node. Right-click the **DoubleAction** orchestration, and then click **Properties**. In the Properties dialog box, click the **Bindings** node, and then set the **Host** to **BizTalkServerApplication** and set the **Receive Port** to **MessageToLOB_ReceivePort**. Click **OK**. Right-click the **DoubleAction** orchestration, and then click **Start**.  
  
## See Also  
 [Creating and Configuring the Fabrikam Solution](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-fabrikam-solution.md)