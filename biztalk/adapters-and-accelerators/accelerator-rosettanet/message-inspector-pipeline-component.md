---
title: "Message Inspector Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, pipelines"
  - "pipelines, custom pipelines"
  - "pipelines, Message Inspector Pipeline Component"
  - "Message Inspector Pipeline Component"
  - "pipelines, creating"
ms.assetid: d9c00718-c8cd-4289-8f58-e4edc61b9a05
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Inspector Pipeline Component
This pipeline component lets you examine all the parts of a multi-part message, and the message context, to determine whether there is a problem with the message. You use this component for troubleshooting purposes.  
  
 The pipeline component drops XML files into a directory that you designate. Each of these files contains one of the four parts of an RNIFv2.0 message (Preamble Header, Delivery Header, Service Header, and Service Content) or the three parts of an RNIFv1.1 message (Preamble Header, Service Header, and Service Content). Another XML file contains the message context.  
  
 You build this component into a custom pipeline and attach it to a send port. You create a filter in the send port to subscribe to the messages that you want to monitor. This troubleshooting occurs in addition to the standard processing that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] already performs.  
  
## Building a Custom Pipeline Using the Message Inspector Pipeline Component  
 To use the Message Inspector Pipeline Component, you have to build and deploy a custom pipeline that includes the component. For more information, see "Creating Pipelines with Pipeline Designer" in BizTalk Server Help.  
  
#### To deploy the Message Inspector Pipeline Component  
  
1. Start Visual Studio.  
  
2. On the **File** menu, point to **Open**, and then click **Project**.  
  
3. Move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component, select **MessageInspector.csproj**, and then click **Open**.  
  
4. Open the Visual Studio command prompt.  
  
5. At the command prompt, move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug.  
  
6. At the command prompt, type **"sn -k MessageInspector.snk"** to create a key, and then press ENTER.  
  
7. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **MessageInspector**, and then click **Properties**.  
  
8. In the **MessageInspector Property**  page, click **Signing** tab, and then click **Sign the assembly** checkbox.  
  
9. In **Choose a strong name key file** drop-down, browse to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug and select **MessageInspector.snk** and then click **Open**.  
  
10. In Solutions Explorer, right-click **MessageInspector**, and then click **Build**. Verify in the Output pane that the build succeeded.  
  
11. Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.  
  
12. In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug, right-click **Microsoft.Solutions.BTARN.SDK.MessageInspector.dll**, and then click **Copy**.  
  
13. Move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Pipeline Components, right-click **Pipeline Components**, and then click **Paste**.  
  
14. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.  
  
15. In the **New Project** dialog box, in the Templates pane, select **Empty BizTalk Server Project**, in the **Name** box, type a name for the project. In the **Location** box, move to the folder that you want to save the project in, and then click **OK**.  
  
16. In Solution Explorer, right-click the project name, point to **Add**, and then click **Add New Item**.  
  
17. In the **Add New Item** dialog box, select **Send Pipeline**, in the **Name** box, type a name for the custom pipeline file, and then click **Open**.  
  
    > [!NOTE]
    >  Add the Message Inspector Pipeline Component only to send ports, not to receive ports.  
  
18. Right-click within the BizTalk Pipeline Components pane of the Toolbox pane, and then click **Add/Remove Items**.  
  
19. In the **Customize Toolbox** dialog box, on the **BizTalk Pipeline Components** tab, select **BTARN Message Inspector Component**, and then click **OK**.  
  
20. In the BizTalk Pipeline Components pane of the Toolbox pane, click and hold **BTARN Message Inspector Component**, and then drag the component on a **Drop Here!** box.  
  
21. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the name of the pipeline project, and then click **Properties**.  
  
22. In the **Property Pages** dialog box, click **Common Properties**, and then click **Assembly**.  
  
23. In the right pane, in the text box associated with **Assembly Key File**, click the ellipses, move to C:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug, select **MessageInspector.snk**, and then click **OK**.  
  
24. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Pipeline Designer, select the **BTARN Message Inspector Component** shape.  
  
25. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Properties window, in the **Directory** box, type the name of the directory to which you want to drop the XML files.  
  
26. In Solution Explorer, right-click the project name, and then click **Build**. Verify that the build succeeds.  
  
27. In Solution Explorer, right-click the project name, and then click **Deploy**. Verify that the deployment succeeds.  
  
28. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **View** menu, click **BizTalk Explorer**.  
  
29. Right-click **Send Ports**, and then click **Add Send Port**.  
  
30. In the **Create New Send Port** dialog box, click **OK**.  
  
31. In the **Send Port Properties** dialog box, in the **Name** box, type a name for the send port, with **Primary** selected in the left pane, click **Transport Type** in the right pane, and select **FILE**.  
  
32. In the **Send Port Properties** dialog box, in the **Address (URI)** box, click the ellipsis button (**...**).  
  
33. In the **FILE Transport Properties** dialog box, type the **Destination** folder name, click **Send** in the left pane, and then for the **Send Pipeline** in the right pane, select the custom pipeline that you have just created.  
  
34. Click **Filters & Maps** in the left pane, and then click **Filters**.  
  
35. Enter a filter expression in the right pane, designating the type of files that you want the pipeline to drop XML files for. For example, if you want to drop files for all RNIF v1.1 messages, for **Property** you would select Microsoft.Solutions.BTARN.Schemas.RNIFv11.GlobalBusinessAction, and for **Operator** you would select "Exists", and then click **OK**.  
  
36. In BizTalk Explorer, right-click the send port that you just created, click **Enlist**, right-click the send port again, and then click **Start**.  
  
## Remarks  
 In typical processing, you can only examine one of the message parts at a time (the part that you have designated as the message body in the orchestration). Therefore, you can only examine one of the parts in the BizTalk Administration Console, and your ability to troubleshoot is limited. The Message Inspector Pipeline Component helps you to overcome this limitation.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
