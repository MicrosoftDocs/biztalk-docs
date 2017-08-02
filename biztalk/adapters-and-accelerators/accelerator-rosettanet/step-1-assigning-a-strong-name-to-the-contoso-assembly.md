---
title: "Step 1: Assigning a Strong Name to the Contoso Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, assigning strong-names"
  - "strong-named assemblies"
ms.assetid: c8ec4593-5a4d-47ab-8799-7b2cd3d15ffc
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Assigning a Strong Name to the Contoso Assembly
In this step, you create and assign a strong name for your BizTalk assembly. A strong name guarantees the uniqueness of an assembly by assigning a digital signature and a unique key pair. Additionally, a strong name provides an integrity check to guarantee that the content of the assembly has not changed since you last built it.  
  
### To create a strong name assembly key file  
  
1.  Start **Visual Studio 2012 Command Prompt**.  
  
2.  At the command prompt, move to the location of the Contoso solution.  
  
    > [!NOTE]
    >  By default, the location of the Contoso solution is *\<drive>*:\Documents and Settings\\*\<user name>*\My Documents\Visual Studio \<version>\Projects.  
  
3.  At the command prompt, type **sn -k FabConPriceAvail.snk**, and then press **Enter**.  
  
4.  At the command prompt, type **Exit**, and then press **Enter**.  
  
### To assign a strong name to your assembly  
  
1.  In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, and then click **Properties**.  
  
2.  In the Property Pages, click **Signing** in the left pane.  
  
3.  In the right pane, select **Sign the assembly**.  
  
4.  Click **Browse** in the Choose the strong name key file field.  
  
5.  Locate your project folder, select the **FabConPriceAvail.snk** file you created earlier, and then click **Open**.  
  
6.  Click **OK** to save the changes.  
  
7.  In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, and then click **Build**. After the build has succeeded, right-click the project again, and then click **Deploy**.  
  
## See Also  
 [Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query/Response Scenario](step-2-create-ports-for-contoso-3a2-price-and-availability-query.md)