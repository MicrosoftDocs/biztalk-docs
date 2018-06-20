---
title: "Adding and Removing Custom Functoids from the Visual Studio Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28f798cc-da97-4332-a842-ba87ac7b13b8
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding and Removing Custom Functoids from the Visual Studio Toolbox
This topic describes how to add custom functoids to and remove custom functoids from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.  
  
## Adding Custom Functoids to Visual Studio  
 Custom functoids must be added to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox before they can be used in a map. Use the following procedure to add custom functoids.  
  
#### To add a custom functoid  
  
1. Add the functoid to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.  
  
   1. Using Windows Explorer, find the assembly that implements your custom functoids.  
  
   2. Copy the assembly to the \<*BizTalk Server installation folder*\>**\Developer Tools\Mapper Extensions** directory. This is where BizTalk Mapper looks for custom functoids.  
  
   3. From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.  
  
   4. In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.  
  
   5. Click **Reset**, and then click **OK**. This process may take a few moments.  
  
       Your custom functoids should now appear in the Toolbox under tabs matching their category.  
  
      \- OR -  
  
   6. From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.  
  
   7. In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.  
  
   8. Click **Reset**, and then click **OK**.  
  
      > [!NOTE]
      >  If your custom functoid does not expose any inline code, make sure its assembly is made available in the global assembly cache.  
  
   9. On the **File** menu, click **Exit** to close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
   10. Start **Visual Studio Command Prompt**.  
  
   11. At the command prompt, type **devenv /setup**.  
  
   12. Start **Microsoft Visual Studio**.  
  
        The custom functoid(s) should appear in the appropriate tab.  
  
2. Add the assembly to the global assembly cache. If your assembly contains only inline functoids, then you can skip this step.  
  
   1.  Start **Visual Studio Command Prompt**.  
  
   2.  Switch to the folder containing your assembly.  
  
   3.  At the command prompt, type **gacutil /if <assembly_path >**. For example, if your assembly name is FunctoidLibrary.dll, then type **gacutil /if FunctoidLibrary.dll**.  
  
   4.  When you are finished, type **exit**.  
  
## Removing Custom Functoids from Visual Studio  
 Use the following procedure to remove custom functoids.  
  
#### To remove a custom functoid  
  
1. Remove the functoid from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.  
  
   1. From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.  
  
   2. In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.  
  
   3. Find the custom functoid in the list, select the **Remove** check box, and then click **OK**.  
  
      \- OR -  
  
   4. While editing a map in a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Toolbox** tab to bring up the Toolbox Palette.  
  
   5. Click the functoid group containing your custom functoid.  
  
   6. Right-click the functoid you want to remove, and then click **Delete** or press the delete key.  
  
2. Remove the functoid assembly from the **Developer Tools\Mapper Extensions** directory.  
  
   > [!CAUTION]
   >  If an assembly contains active functoids, then do not remove it. Doing so will break other maps.  
  
   1. Start Windows Explorer and navigate to the **Developer Tools\Mapper Extensions** directory of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
   2. Right-click the assembly containing the removed functoid, and then click **Delete** to remove the file.  
  
3. Remove the functoid assembly from the global assembly cache. If your assembly contains only inline functoids, then you can skip this step.  
  
   > [!CAUTION]
   >  If an assembly contains active functoids, then do not remove it from the global assembly cache. Doing so will break other maps.  
  
   1.  Start **Visual Studio Command Prompt**.  
  
   2.  At the command prompt, type **gacutil /u <assembly_display_name>**. For example, if your assembly name is FunctoidLibrary.dll, then type **gacutil /if FunctoidLibrary**.  
  
   3.  When you are finished, type **exit**.  
  
## See Also  
 [Developing Custom Functoids](../core/developing-custom-functoids.md)