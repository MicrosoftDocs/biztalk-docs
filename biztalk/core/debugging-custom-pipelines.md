---
title: "Debugging Custom Pipelines | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27e5445a-6415-4c52-a450-b74a71fc4aa2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Debugging Custom Pipelines
When message processing fails in your custom pipeline, you can use source level debugging to identify and correct problems. Source level debugging is done using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] debugger by attaching to BTSNTSVC.exe (if the custom pipeline is deployed) or Pipeline.exe (if using the stand-alone pipeline tool).  
  
## Procedures  
 Use the following procedures to debug custom pipelines.  
  
### How to Debug a Deployed Pipeline  
 Tracking queries from the Group Hub page, and the event viewers, provide useful information about message processing failures in deployed components. This information can often be used to narrow down the origin of a problem. Once a custom pipeline has been implicated, source level debugging can be used to identify any problematic code.  
  
##### To Debug a Deployed Custom Pipeline using Visual Studio  
  
1. Load the custom pipeline project solution into [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. Change the output path for your solution to *\<Installation Folder\>*\Pipeline Components. In Solution Explorer, right-click your project, click the Build tab, and then change the Output Path by clicking the **Browse** button and selecting the *\<Installation Folder\>*\Pipeline Components directory.  
  
3. From within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], deploy the solution by clicking **Build** &#124; **Deploy**.  
  
4. Restart the host instance that runs the pipeline. Using the BizTalk Server Management console, navigate to the host instance that runs the pipeline, right-click the host instance then click **Restart**.  
  
5. Attach the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] debugger to BTSNTSVC.exe. This can be done by clicking **Debug** &#124; **Attach to Process**, click Show processes in all sessions, and then double-click BTSNTSVC.exe.  
  
6. Set breakpoints.  
  
7. Drop a message in the appropriate location to initiate the custom pipeline component. Processing should halt on the breakpoints you set.  
  
> [!NOTE]
>  If your code throws an exception, BizTalk Server will catch it and ultimately suspend the message. To avoid this behavior, you should break on first chance exceptions.  
  
### How to Debug Using Pipeline.exe  
 You can also test custom pipelines using Pipeline.exe. This has the advantage of not requiring you to deploy the pipeline at the expense of not running under conditions similar to production.  
  
> [!NOTE]
>  If your custom pipeline uses the flat file assembler / disassembler, Pipeline.exe will not execute properly. This is because Pipeline.exe does not access the BizTalk database. One solution is to remove the assembler / disassembler components and test them separately with FFDasm.exe and FFAsm.exe. See [Pipeline Tools](../core/pipeline-tools.md) for more information.  
  
##### To Debug a Custom Pipeline using Pipeline.exe and Visual Studio  
  
1. Load the custom pipeline project solution into [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. Change the output path for your solution to *\<Installation Folder\>*\Pipeline Components. In Solution Explorer, right-click your project, click the Build tab, and then change the Output Path by clicking the **Browse** button and selecting the *\<Installation Folder\>*\Pipeline Components directory.  
  
3. Change the start action for your solution. In Solution Explorer, right-click your project, click the Debug tab, click Start external program, then click **…** and navigate to *\<Installation Folder\>*\SDK\Utilities\PipelineTools and choose Pipeline.exe. Under Start Options, enter the command line arguments appropriate for your component. For more information on Pipeline.exe, see [Pipeline Tools](../core/pipeline-tools.md). A typical configuration specifies the pipeline and a sample file:  
  
   ```  
   <Path>\YourPipeline.btp -d <Path>\YourTestFile.txt -c  
   ```  
  
4. Set your breakpoints.  
  
5. Press F5 to begin debugging.  
  
## See Also  
 [Pipeline Tools](../core/pipeline-tools.md)