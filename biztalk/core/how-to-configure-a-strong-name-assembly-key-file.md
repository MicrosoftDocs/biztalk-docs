---
title: "How to Configure a Strong Name Assembly Key File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5778a8ec-f5f7-4ae1-a57e-99f6503f044c
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a Strong Name Assembly Key File
In the process of deploying a BizTalk solution, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] first builds the assemblies. The deployment process requires that each assembly is strongly signed. You can strongly sign your assemblies by associating the project with a strong name assembly key file. If you haven't already done so, before deploying a solution from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], use the following procedure to generate a strong name assembly key file and assign it to each project in the solution.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator's group. In addition, your account must have Write permissions on the global assembly cache (GAC). The Administrators account on the local computer has this permission.  
  
### To configure a strong name assembly key file  
  
1. Start **Visual Studio Command Prompt**.  
  
2. At the command prompt, from the folder where you want to store the key file, type the following command, and then press ENTER:  
  
    **sn /k**  *file_name* **.snk**  
  
    Example: **sn /k ErrorHandling.snk**  
  
    A confirmation message, **Key pair written to** \<*file_name*\>**.snk**`,` displays on the command line.  
  
3. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the project and then click **Properties**.  
  
4. Click the **Signing** tab and choose **Browse** in the **Choose a strong name key file** drop down box.  
  
5. Browse to the key file and click it. Click **Open**, and then close the project properties.  
  
6. Repeat steps 3 through 6 for each project in the solution that you want to deploy using this strong name assembly key file.  
  
## See Also  
 [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)