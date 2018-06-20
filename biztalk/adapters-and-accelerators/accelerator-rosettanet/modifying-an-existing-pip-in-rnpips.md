---
title: "Modifying an Existing PIP in RNPIPs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RNPIPs"
  - "modifying, PIPs"
  - "PIPs, modifying"
  - "assemblies, RNPIPs"
ms.assetid: f2ed25c4-1979-4691-9315-e7568e7cca8b
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Modifying an Existing PIP in RNPIPs
This topic describes how to change and re-deploy one of the Partner Interface Process (PIP) schemas installed by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] setup. You deploy the schema as part of the RNPIPs assembly.  
  
### To modify an existing PIP in RNPIPs  
  
1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Locate the \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Utilities\Schema Generator folder.  
  
3. At the command prompt, type **CScript InstallDTD.vbs**, and then press ENTER.  
  
   > [!NOTE]
   >  You only have to do steps 1 and 2 one time after you install BizTalk Server.  
  
4. Start **Microsoft Visual Studio 2012**.  
  
5. In the **File** menu, point to **Open**, and then click **Project**.  
  
6. In the **Open Project** dialog box, move to \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas, and then select **RNPIPs.btproj**.  
  
7. In the **View** menu, click **BizTalk Explorer**. Expand **Assemblies**, and then right-click **Microsoft.Solutions.BTARN.Schemas.RNPIPs(3.3.0.0)**. Click **Undeploy**.  
  
8. Start **Visual Studio 2012 Command Prompt**.  
  
9. Move to the location entered in step 6, at the command prompt, type **sn -k RNPIPs.snk**, and then press **Enter**.  
  
10. In Solution Explorer, right-click **RNPIPs**, click **Properties**, click **Common Properties**, and then click **Assembly.**  
  
11. In the right pane, scroll down to **Strong Name**, in the **Assembly Key File** section, click the ellipsis button (...) button, go to the location entered in step 6, at the command prompt, type **RNPIPs.snk**, and then click **OK**.  
  
12. In the **Property Pages** dialog box, click **Configuration Properties**, click **Deployment**, click **Redeploy**, select `True`, and then click **OK**.  
  
13. Edit any of the existing schemas in RNPIPs, as required.  
  
14. Click **File**, and then click **Save**.  
  
15. Right-click the project name, and then click **Build**.  
  
16. Right-click the project name, and then click **Deploy**.  
  
17. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
18. In BizTalk Administration Console, expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, and then expand **Hosts**.  
  
19. In the right pane, right-click the name of the host, and then click **Stop**. After the service has stopped, right-click the name of the host, and then click **Start**.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)