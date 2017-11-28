---
title: "Stop Orchestration (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, examples"
  - "examples, orchestrations"
  - "orchestrations, stopping"
ms.assetid: 83be44e9-819d-4ac5-8b75-84c23e6b5ba2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Stop Orchestration (BizTalk Server Sample)
The Stop Orchestration sample demonstrates how to stop a BizTalk Server orchestration and, optionally, to unenlist it.  
  
> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.  
  
## What This Sample Does  
 The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:  
  
-   Given an orchestration name and an assembly name, query for a specific deployed BizTalk Server orchestration.  
  
-   Stop that orchestration.  
  
-   Unenlist that orchestration (optionally).  
  
-   Handle any errors such that meaningful information is returned to the user.  
  
## Where to Find This Sample  
 The sample files are located in the following SDK location:  
  
 \<*Samples Path*\>\Admin\WMI\Stop Orchestration\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the \VBScript folder:<br /><br /> StopOrch.vbs|VBScript file that takes parameters to specify an orchestration to be stopped and, optionally, unenlisted.|  
  
## Building and Initializing This Sample  
 The Stop Orchestration sample consists of a single VBScript file that you do not need to build or initialize.  
  
## Running This Sample  
  
#### To run this sample  
  
1.  In a command window, navigate to the following folder:  
  
     \<*Samples Path*\>\Admin\WMI\Stop Orchestration\VBScript\  
  
2.  Run the file StopOrch.vbs using the cscript program, passing the following command-line arguments, of which the third one is optional:  
  
    -   **\<**
         ***OrchestrationName* \>.** The name of the BizTalk Server orchestration to be stopped and, optionally, unenlisted.  
  
    -   **\<**
         ***AssemblyName* \>.** The name of the BizTalk assembly in which the specified orchestration was deployed. If the assembly name contains spaces, enclose the name in quotes.  
  
    -   **Unenlist.** An optional, literal string used to indicate that the specified orchestration should be unenlisted in addition to being stopped.  
  
         For example:  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         -OR-  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration MyBusinessAssembly Unenlist  
        ```  
  
## Comments  
 All tasks that you can perform in the BizTalk Server Administration console can also be performed by using scripts that access the Windows WMI object model.  
  
 The script file StopOrch.vbs contains detailed comments with further explanation about the operations that it performs. For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## See Also  
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)