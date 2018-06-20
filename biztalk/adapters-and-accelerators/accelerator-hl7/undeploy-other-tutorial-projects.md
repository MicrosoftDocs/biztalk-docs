---
title: "Undeploy Other Tutorial Projects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fce837f-1853-4d5d-a680-8ae2a974c750
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Undeploy Other Tutorial Projects
When you deploy a BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) tutorials, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] stores the tutorial assembly files in the Configuration database (also known as the BizTalk Management database) and the global assembly cache. If you have run another [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] tutorial, and deployed the assemblies that you created in that tutorial, you may encounter errors when you test your assemblies in the three parts of the Batching tutorial. This may occur because you can only deploy one message schema at one time.  
  
 You can avoid these errors by undeploying assemblies that you deployed in previous tutorials. You can re-deploy the assembly later if needed.  
  
 Before undeploying an assembly, you need to unenlist orchestrations in the assembly. You also need to remove any reference to the assembly that you want to undeploy, from any other assembly that you want to keep deployed. An alternative is to delete all DLLs associated with one tutorial, before starting another tutorial.  
  
### To undeploy an assembly  
  
1. Unenlist orchestrations used in the assembly that you want to undeploy by clicking the orchestration in BizTalk Explorer of Visual Studio, and then clicking **Unenlist**.  
  
2. In any assembly that you want to keep deployed, remove references to assemblies that you want to undeploy. Right click the reference in Solution Explorer, and then click **Remove**.  
  
3. Open BizTalk Explorer, right-click the assembly that you want to undeploy, and then click **Undeploy**.  
  
   For more information about undeploying an assembly, see "Undeploying an Assembly Using BizTalk Explorer" in BizTalk Server Help.  
  
## See Also  
 [Preparing to Use the Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)