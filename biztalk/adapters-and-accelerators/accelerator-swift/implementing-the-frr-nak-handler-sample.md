---
title: "Implementing the FRR NAK Handler Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80fa5fb7-6864-4923-b641-e76d2b95d923
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing the FRR NAK Handler Sample
To implement the sample FRR NAK custom handler, add the sample project to your solution, build and deploy the project, bind and start the orchestration, and then stop and restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  

### To implement the FRR NAK Custom Handler  

1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], open your solution. In Solution Explorer, right-click the solution, point to **Add**, and then click **Existing Project**.  

2. In the **Add Existing Project** dialog box, move to *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Samples\FrrHandler. Select **RepairSWIFTRejectedMessage.btproj**, and then click **Open**.  

3. Generate a key and assign the key to the project.  

4. Build and deploy the RepairSWIFTRejectedMessage.btproj project.  

5. In BizTalk Explorer, expand **BizTalk Configuration Databases**, **\<*server name*\>,BizTalkMgmtDb.dbo**, and **Orchestrations**, right-click **RepairSWIFTRejectedMessage.Orchestration_1**, and then click **Bind**.  

6. In the **Port Binding Properties** dialog box, select your host, such as BizTalkServerApplication, and then click **OK**.  

7. In BizTalk Explorer, right-click **RepairSWIFTRejectedMessage.Orchestration_1**, and then click **Start**.  

8. In the **Express Start** dialog box, click **OK**.  

9. Click **Start**, and then click **Run**. Enter **services.msc**, and then click **OK**. Right-click **BizTalk Service**, and then click **Restart**.
