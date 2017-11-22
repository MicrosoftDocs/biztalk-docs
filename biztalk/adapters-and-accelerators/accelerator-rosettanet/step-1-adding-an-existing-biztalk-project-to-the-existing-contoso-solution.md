---
title: "Step 1: Adding an Existing BizTalk Project to the Existing Contoso Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projects, adding to solutions"
  - "private process tutorial, adding projects to solutions"
ms.assetid: 9e84d282-01aa-4611-8462-c1acef234042
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Adding an Existing BizTalk Project to the Existing Contoso Solution
The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK contains a private process orchestration that serves as a good starting point when customizing your own private process. In this step, you add that orchestration to your solution and change the assembly name to avoid conflict with the PrivateResponder orchestration installed during the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] installation. Before you start, open the Contoso solution you created in [Step 1: Creating a New BizTalk Solution for the Contoso Price and Availability Request](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-new-biztalk-solution-for-contoso-price-and-availability-request.md).  
  
### To add the PrivateResponder project to the Contoso solution  
  
1.  Copy the PrivateResponder SDK sample to your Contoso solution folder.  
  
    > [!NOTE]
    >  By default, the PrivateResponder SDK sample is located in the C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder folder.  
  
2.  In Visual Studio, click **File**, point to **Add**, and then click **Existing Project**.  
  
3.  In the Add Existing Project dialog box, locate the folder for your solution, select the **PrivateResponder.btproj** project file, and then click **Open**.  
  
### To change the PrivateResponder assembly name and default namespace  
  
1.  In Solution Explorer, right click the **PrivateResponder** project, and then click **Properties**.  
  
2.  In the PrivateResponder Property Pages dialog box, in the console tree, click **General**. In the details pane, in the **Assembly Name** box, type **ContosoPriceAndAvailability.PrivateResponder**.  
  
3.  In the **Default Namespace** box, type **ContosoPriceAndAvailability**.  
  
4.  Click **OK** to close the PrivateResponder Property Pages dialog box.  
  
5.  In Solution Explorer, double-click **PrivateResponder.odx**.  
  
6.  In the **Orchestration View** window, ensure that **Orchestration Properties** (under **PrivateResponderProcess**) is selected.  
  
7.  In the **Properties** window, in the **Namespace** field, type **ContosoPriceAndAvailability**, and then press **Enter**.  
  
## See Also  
 [Step 2: Defining and Publishing the Vocabulary for Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-2-defining-and-publishing-the-vocabulary-for-contoso.md)