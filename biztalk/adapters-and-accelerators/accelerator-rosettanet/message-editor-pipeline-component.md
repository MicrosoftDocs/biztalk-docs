---
title: "Message Editor Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, Message Editor Pipeline Component"
  - "Message Editor Pipeline Component"
  - "messages, editing"
  - "pipelines, Message Editor Pipeline Component"
ms.assetid: f2b22dea-54e8-410b-868f-2978139f438b
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Editor Pipeline Component
This component lets you edit automatically any part of a multipart message within a send or receive pipeline. You add this component to an existing pipeline to set up the replacement as part of typical processing.  
  
## Building the Message Editor Pipeline Component into an Existing Pipeline  
 To use the Message Editor Pipeline Component, you have to add the component to an existing pipeline. For more information, see "Creating Pipelines with Pipeline Designer" in BizTalk Server Help.  
  
#### To add the Message Editor Pipeline Component to an existing pipeline  
  
1. Start Visual Studio.  
  
2. On the **File** menu, point to **Open**, and then click **Project**.  
  
3. Move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Editor Pipeline Component, select **MessageEditor.csproj**, and then click **Open**.  
  
4. Start Visual Studio command prompt.  
  
5. At the command prompt, move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug.  
  
6. At the command prompt, type **sn -k MessageEditor.snk** to create a key, and then press ENTER.  
  
7. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **MessageEditor**, and then click **Properties**.  
  
8. In the **MessageEditor Property** page, click **Signing** tab, and then click **Sign the assembly** checkbox.  
  
9. In **Choose a strong name key file** drop-down, browse to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\ SDK\Message Editor Pipeline Component\obj\debug and select **MessageEditor.snk** and then click **Open**.  
  
10. In Solution Explorer, right-click **MessageEditor**, and then click **Build**. Verify in the Output pane that the build succeeded.  
  
11. Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.  
  
12. In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug, right-click **Microsoft.Solutions.BTARN.SDK.MessageEditor.dll**, and then click **Copy**.  
  
13. Move to C:\Program Files\Microsoft BizTalk Server 2013\Pipeline Components, right-click **Pipeline Components**, and then click **Paste**.  
  
14. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project**.  
  
15. Open the project that contains the pipeline to which you want to add the editor.  
  
16. In Solution Explorer, double-click the pipeline name to open the pipeline in Pipeline Designer.  
  
17. Right-click in the BizTalk Pipeline Components pane of the Toolbox pane, and then click **Add/Remove Items**.  
  
18. In the **Customize Toolbox** dialog box, on the **BizTalk Pipeline Components** tab, select **BTARN Message Editor Component**, and then click **OK**.  
  
19. In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Editor Component**, and then drag the component to the position that you want in the pipeline.  
  
20. In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Editor Component**, and then drag the component to the position that you want in the pipeline.  
  
    > [!NOTE]
    >  It is recommended that you add the Message Editor Pipeline Component after the Disassemble stage in the receive pipeline component or in the Pre-Assemble stage of the send pipeline component.  
  
21. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Pipeline Designer, select the **BTARN Message Editor Component** shape.  
  
22. In the Properties pane, in the text box associated with **XPath Query**, type the name of the XPath element for which you want to change the value.  
  
23. In the text box associated with **XPath Value**, type the value to which you want to set the XPath element.  
  
24. In Solutions Explorer, right-click the project name, and then click **Build**. Verify that the build succeeds.  
  
25. In Solutions Explorer, right-click the project name, and then click **Deploy**. Verify that the deployment succeeds.  
  
## Example  
 To change the value of the element `ProprietaryDocumentIdentifier` in the 0C1 PIP Schema, add the XPath Query shown in the following Code section to the XPath Query property of the Message Editor Pipeline Component.  
  
```  
/*[local-name()='Pip0C1AsynchronousTestNotification' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='thisDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='ProprietaryDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']  
```  
  
 To obtain a complete XPath Query, open the schema in BizTalk Editor, and then copy the Xpath from the `Instance XPath` property under the Properties window. The XPath Query that you provide should have all the namespace references in it.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
