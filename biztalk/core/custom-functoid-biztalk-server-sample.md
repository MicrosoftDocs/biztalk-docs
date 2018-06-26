---
title: "Custom Functoid (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoids, customizing"
  - "examples, functoids"
  - "functoids, examples"
  - "XML tools"
  - "examples, XML tools"
ms.assetid: 9f1eb260-ff62-46f5-a517-57f4e9172b35
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Functoid (BizTalk Server Sample)
The Custom Functoid sample demonstrates how to write a custom functoid for BizTalk Mapper. You can add the functoid to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox. The functoid will be displayed in the Toolbox when BizTalk Mapper is in focus.  
  
 A custom functoid should reside in a BizTalk Mapper assembly to recognize it. It can be written in any .NET-compliant language, such as C# or Visual Basic.  
  
 Also, a custom functoid must derive from the `Microsoft.BizTalk.BaseFunctoids` class, and it must provide implementation for some methods by overriding them. (The `BaseFunctoid` class is defined in the Microsoft.BizTalk.BaseFunctoids.dll assembly included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)  
  
## What This Sample Does  
 The Custom Functoid sample implements several functoids, each deriving from the `BaseFunctoid` class and overriding several methods.  
  
 When implementing a custom functoid, you can expose its code inline. The inline code is what performs the computation for the functoid. The BizTalk Mapper compiler extracts inline code from a functoid and embeds it in the compiled XSLT when you build the project.  
  
 If your custom functoid does not expose any inline code, BizTalk Mapper generates XSLT that calls into the assembly where the custom functoid resides. In this case, you must be sure your custom functoid assembly is available in the global assembly cache (GAC) so the XSLT engine can find it. A custom functoid must also have a unique GUID attribute. BizTalk Mapper uses the GUID to identify which assembly to load.  
  
> [!IMPORTANT]
>  If you reuse the Custom Functoid sample code to implement your own functoid(s), you must be sure to change the GUID attribute to one that is unique.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\XmlTools\CustomFunctoid  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|Assembly information C# source code.|  
|CBuildArray.bmp|Toolbox bitmap.|  
|CConcat.bmp|Toolbox bitmap.|  
|CExtractArray.bmp|Toolbox bitmap.|  
|Cleanup.bat|Used to undeploy assemblies and remove them from the global assembly cache (GAC) and to delete CustomFunctoid.dll.|  
|CLongestString.bmp|Toolbox bitmap.|  
|CMultiply.bmp|Toolbox bitmap.|  
|CustomFunctoid.cs|Custom functoid C# source code.|  
|CustomFunctoid.csproj|Custom functoid C# project.|  
|CustomFunctoid.sln|Custom functoid solution.|  
|CustomFunctoidResources.resx|Custom functoid resources.|  
|Setup.bat|Used to build, deploy, and start the sample.|  
  
## Building and Initializing This Sample  
 Use the following procedure to build and initialize the Custom Functoid sample.  
  
#### To build and initialize this sample  
  
1.  In a command window, change directory (**cd**) to the following folder:  
  
     \<*Samples Path*\>\XmlTools\CustomFunctoid  
  
2.  Run the file Setup.bat, which performs the following actions:  
  
    -   Builds the sample project.  
  
    -   Copies the generated assembly to the Developer Tools\Mapper Extensions directory.  
  
    -   Adds the generated assembly to the GAC.  
  
        > [!NOTE]
        >  You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.  
  
## Running This Sample  
 Use the following procedure to run the Custom Functoid sample.  
  
#### To run this sample  
  
1. From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Tools** menu, and select **Choose Toolbox Items**.  
  
2. In the **Choose Toolbox items** dialog box, select the **BizTalk Mapper Functoids** tab.  
  
3. Click **Reset**, and then click **OK**.  
  
   > [!NOTE]
   >  If your custom functoid does not expose any inline code, make sure its assembly is made available in the GAC.  
  
4. From the **File** menu, select **Exit** to close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
5. Start **Visual Studio Command Prompt**.  
  
6. At the command prompt, type **devenv /setup**.  
  
7. Start **Microsoft Visual Studio**.  
  
    The custom functoids (Custom concatenate functoid, Longest String, Build array functoid, and Extract array functoid) appear on the **String Functoids** tab of the Toolbox, and the Cumulative Multiply functoid appears on the **Cumulative Functoids** tab.  
  
## Removing This Sample  
 Use the following procedure to remove the Custom Functoid sample.  
  
#### To remove this sample  
  
1. Remove the functoids from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.  
  
   > [!WARNING]
   >  If after running Cleanup.bat, you still see the stale custom functoids in the toolbox (probably due to internal caching by Visual Studio), then follow the procedures below:  
  
   1. From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Tools** menu, and select **Choose Toolbox Items**.  
  
   2. In the **Choose Toolbox items** dialog box, select the **BizTalk Mapper Functoids** tab.  
  
   3. Find the custom functoids (Custom concatenate functoid, Longest String, Build array functoid, Extract array functoid, and Cumulative Multiply) in the list. Click the respective **check box** to remove the functoids, and then click **OK**.  
  
      If the above procedure does not work, follow the below procedure.  
  
   4. From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Toolbox** tab while editing a map to bring up the Toolbox Palette.  
  
   5. Right-click the tool box and select **Choose Items**.  
  
   6. In the Choose Items dialog box, click **Reset**, and then click **OK**.  
  
   7. Close all instances of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
      If the above procedure does not work, follow the below procedure.  
  
   8. Start **Visual Studio Command Prompt** as an administrator.  
  
   9. Close all the running instances of Visual Studio.  
  
   10. Give the following commands:  
  
        `devenv /resetsettings`  
  
        `devenv /setup`  
  
   11. You can manually select the unwanted functoids from the toolbox. Then, right click the functoid, and click **Delete**.  
  
       If the above procedure does not work, follow the below procedure.  
  
   12. From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the Toolbox tab while editing a map to bring up the Toolbox Palette.  
  
   13. Click the **Cumulative Functoids** group.  
  
   14. Right click the functoid you want to remove and then choose **Delete** or press the delete key.  
  
   15. Click the **String Functoids** group.  
  
   16. Right click the functoid you want to remove and then choose **Delete** or press the delete key.  
  
2. In a command window, change directory (**cd**) to the following folder:  
  
    \<*Samples Path*\>\XmlTools\CustomFunctoid  
  
3. Run the file Cleanup.bat, which performs the following actions:  
  
   -   Deletes the assembly from the Developer Tools\Mapper Extensions directory.  
  
   -   Removes the assembly from the GAC.  
  
## Classes or Methods Used in This Sample  
 [Microsoft.BizTalk.BaseFunctoids.BaseFunctoid](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.basefunctoid.aspx)  
  
## See Also  
 [Using BaseFunctoid](../core/using-basefunctoid.md)   
 [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md)