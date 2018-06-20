---
title: "Customizing a Private Process to Work with a Specific PIP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private processes, PIPs"
  - "private processes, customizing"
  - "developing, private processes"
  - "PIPs, private processes"
  - "customizing private processes"
ms.assetid: 88494e87-25a0-4c94-9396-61a0e07964aa
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Customizing a Private Process to Work with a Specific PIP
You can create a filter expression that will cause a responder private-process orchestration to process or not process instances of a specific Partner Interface Process (PIP). This gives you the flexibility of creating a custom private process to receive and process some PIP instances, and using the default private process to process all other PIP instances.  
  
 To create a custom private process to work with a specific PIP or multiple specific PIPs, you create a filter expression for the receive shape of the private-process orchestration. An example is the PIP3A4PrivateResponder.odx orchestration in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK. It is located at \<*drive*\>:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PIP3A4Process Using Business Rules\PIP3A4PrivateResponder.  
  
 Besides creating a private process that process only instances of a specific PIP, you must customize the default BTARN private process so that it will not process instances for that PIP.  
  
### To customize a responder private process to work with a specific PIP  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], create a custom responder private-process orchestration for working with a specific PIP. You can base the orchestration on the default BTARN responder private-process orchestration.  
  
   > [!NOTE]
   >  You can find the default responder private-process orchestration, named PrivateResponder.odx, in the BTARN SDK. It is located at *\<drive\>*:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder.  
  
2. Add the custom orchestration to your BizTalk project. Make sure that your project has a reference to the Microsoft.Solutions.BTARN.GlobalSchemas.dll file.  
  
3. Open the custom orchestration in Orchestration Designer.  
  
4. Right-click the first **Receive** shape that activates the orchestration, and then click **Edit Filter Expression**.  
  
   > [!NOTE]
   >  The receive shape for the default BTARN responder private-process orchestration has two filter conditions: Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "AsyncAction" or Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == "SyncAction". This expression makes sure that the orchestration processes RosettaNet messages. Retain this filter expression in your custom orchestration.  
  
5. In the **Filter Expression** dialog box, in the Property column in the first open row, select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list, in the Operator column, select **==** from the drop-down list, in the Value column, type the three-digit PIP code, for example, type **3A4**.  
  
6. Click **OK**.  
  
7. Open the default responder private-process orchestration project (PrivateResponder.btproj) in Orchestration Designer. Make sure that the project has a working reference to the Microsoft.Solutions.BTARN.GlobalSchemas.dll file.  
  
8. Double-click **PrivateResponder.odx**.  
  
9. Right-click the **ReceiveFromPublicProcessResponder** receive shape, and then click **Edit Filter Expression**.  
  
10. In the **Filter Expression** dialog box, in the Property column in the first open row, select **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** from the drop-down list. In the Operator column, select **!=** from the drop-down list. In the Value column, type the three-digit PIP code, for example, type "**3A4"**.  
  
11. Click **OK**.  
  
12. In Solution Explorer, right-click the project that contains the orchestration and then click **Build**.  
  
13. After the project has been successfully built, right-click the project, and then click **Deploy**.  
  
14. On the **File** menu, point to **Open**, and then click **Project**.  
  
15. Move to \<*drive*\>:\Program Files\BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder, select **PrivateResponder.odx**, and then click **OK**.  
  
16. In Solution Explorer, right-click the project, and then click **Build**.  
  
17. After the project has been successfully built, right-click the project, and then click **Deploy**.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)