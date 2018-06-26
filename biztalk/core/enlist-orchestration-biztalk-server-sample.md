---
title: "Enlist Orchestration (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, examples"
  - "orchestrations, enlisting"
  - "examples, orchestrations"
ms.assetid: d8d53e59-2313-40dd-a278-0a29d8eb4ce8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enlist Orchestration (BizTalk Server Sample)
The Enlist Orchestration sample demonstrates how to enlist a BizTalk Server orchestration to a host.  
  
> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.  
  
## What This Sample Does  
 This sample includes a Visual Basic Scripting Edition (VBScript) version that accesses the Windows Management Instrumentation (WMI) object model, and a Visual C# version that accesses the **System.Management** objects provided by the .NET Framework. Both of these versions ultimately access the BizTalk Server WMI provider to perform the following operations:  
  
-   Given an orchestration name and an assembly name, query for a specific deployed BizTalk Server orchestration.  
  
-   Enlist that orchestration to the default host.  
  
-   Handle any errors such that meaningful information is returned to the user.  
  
## Where to Find This Sample  
 The samples are located in the following SDK locations:  
  
- VBScript version: \<*Samples Path*\>\Admin\WMI\Enlist Orchestration\VBScript\  
  
- Visusal C# version: \<*Samples Path*\>\Admin\WMI\Enlist Orchestration\CSharp\  
  
  The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the \VBScript folder:<br /><br /> EnlistOrch.vbs|VBScript file that takes parameters to specify an orchestration to be enlisted to a host.|  
|In the \CSharp folder:<br /><br /> App.ico, AssemblyInfo.cs, BTSampleEnlistOrc.csproj, BTSampleEnlistOrc.sln, EnlistOrc.cs|Project, solution, and source files for building a Visual C# command-line application that takes parameters to specify an orchestration to be enlisted to a host.|  
  
## Building and Initializing This Sample  
 The VBScript version of the Enlist Orchestration sample consists of a single Visual Basic script file that you do not need to build or initialize.  
  
#### To build the Visual C# version of the Enlist Orchestration sample  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file BTSampleEnlistOrc.sln.  
  
2. In the **Build** menu, click **Build Solution**.  
  
#### To run the Enlist Orchestration sample.  
  
1.  In a command window, navigate to one of the following folders, depending on whether you are planning to run the VBScript version or the Visual C# version of this sample, respectively:  
  
     \<*Samples Path*\>\Admin\WMI\Enlist Orchestration\VBScript\  
  
     \<*Samples Path*\>AdminWMIEnlist OrchestrationCSharpbinDebug  
  
2.  Either run the file EnlistOrch.vbs using the cscript program, or run the file EnlistOrc.exe, depending on whether you are planning to run the VBScript version or the Visual C# version of this sample, respectively. In any event, pass the following command-line arguments:  
  
    -   **\<**
         ***OrchestrationName* \>.** The name of the orchestration to be enlisted.  
  
    -   **\<**
         ***AssemblyName* \>.** The name of the assembly in which the orchestration was deployed. If the assembly name contains spaces, enclose the name in quotes.  
  
         For example: (VBScript):  
  
        ```  
        cscript EnlistOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         -OR- (Visual C#):  
  
        ```  
        EnlistOrc MyBusinessOrchestration "My Business Assembly"  
        ```  
  
## Comments  
 All tasks that you can perform in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console can also be performed by using script that accesses the Windows WMI object model and by using Visual C# that accesses the **System.Management** objects provided by the .NET Framework.  
  
 The script file EnlistOrch.vbs and the Visual C# source file EnlistOrc.cs contain detailed comments with further explanation about the operations that they perform. For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## See Also  
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)