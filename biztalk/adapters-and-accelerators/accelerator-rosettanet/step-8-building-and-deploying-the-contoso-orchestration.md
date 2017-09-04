---
title: "Step 8: Building and Deploying the Contoso Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, building solutions"
  - "private process tutorial, deploying solutions"
ms.assetid: d350b87a-0e4e-4837-ad39-fb5b1fdc1532
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8: Building and Deploying the Contoso Orchestration
In this step, you build the Orchestration project and deploy it using the BizTalk Deployment Wizard. This adds the assembly to the Configuration database and installs the assembly in the Global Assembly Cache (GAC).  
  
### To assign a strong name to your assembly  
  
1.  In Solution Explorer, right-click the **PrivateResponder** project, and then click **Properties**.  
  
2.  In the PrivateResponder Property Pages dialog box, select **Assembly** from the left pane.  
  
3.  In the right pane, scroll down to the **Strong name** section, click the field to the right of the **Assembly Key File**, and then click the ellipsis button (**…**).  
  
4.  Locate your project folder, select the **FabConPriceAvail.snk** file, and then click **Open**.  
  
5.  In the right pane, select **False** from the **Assembly Delay Sign** drop down list.  
  
6.  Click **OK** to save the changes.  
  
### To build and deploy the orchestration project  
  
1.  In Solution Explorer, right-click the **PrivateResponder** project, and then click **Build**.  
  
    > [!NOTE]
    >  You can safely ignore any warnings that occur during the build process.  
  
2.  After the build has succeeded, right-click the project again, and then click **Deploy**.  
  
## See Also  
 [Step 9: Starting the Contoso Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/step-9-starting-the-contoso-orchestration.md)