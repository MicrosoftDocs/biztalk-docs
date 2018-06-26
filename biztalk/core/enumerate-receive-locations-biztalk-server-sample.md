---
title: "Enumerate Receive Locations (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, examples"
  - "receive locations, enumerating"
  - "examples, receive locations"
ms.assetid: 27ff8ac6-7e8e-4dde-84d1-d21bf417ddd7
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enumerate Receive Locations (BizTalk Server Sample)
The Enumerate Receive Locations sample demonstrates how to retrieve details about one or more receive locations.  
  
> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.  
  
## What This Sample Does  
 This sample includes a Visual Basic Scripting Edition (VBScript) version that accesses the Windows WMI object model, and a Visual C# version that accesses the **System.Management** objects provided by the .NET Framework. Both of these versions ultimately access the BizTalk Server WMI provider to perform the following operations:  
  
-   Query for the set of configured receive locations or for a specific receive location, given its name.  
  
-   Retrieve and display details about each receive location of interest.  
  
-   Handle any errors such that meaningful information is returned to the user.  
  
## Where to Find This Sample  
 The samples are located in the following SDK locations:  
  
- VBScript version: \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\VBScript\  
  
- Visual C# version: \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\CSharp\  
  
  The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the \VBScript folder:<br /><br /> EnumRecLocs.vbs|VBScript file that retrieves details about all configured receive locations.|  
|In the \CSharp folder:<br /><br /> App.ico, AssemblyInfo.cs, BTSampleEnumerateRLs.csproj, BTSampleEnumerateRLs.sln, EnumRLs.cs|Project, solution, and source files for building a Visual C# command-line application that retrieves details about all configured receive locations, or about a specific receive location.|  
  
## Building and Initializing This Sample  
 The VBScript version of the Enumerate Receive Locations sample consists of a single Visual Basic script file that you do not need to build or initialize.  
  
#### To build the Visual C# version of the Enumerate Receive Locations sample  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file BTSampleEnumerateRLs.sln.  
  
2. In the **Build** menu, click **Build Solution**.  
  
## Running This Sample  
  
#### To run the Enumerate Receive Locations sample  
  
1.  In a command window, navigate to one of the following folders, depending on whether you are going to run the VBScript version or the Visual C# version of this sample, respectively:  
  
     \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\VBScript\  
  
     \<*Samples Path*\>\Admin\WMI\Enumerate Receive Locations\CSharp\bin\Debug\  
  
2.  Either run the file EnumRecLocs.vbs using the cscript program, or run the file EnumRl.exe, depending on whether you are going to run the VBScript version or the Visual C# version of this sample, respectively. For the Visual C# version, pass one of the following two command-line arguments:  
  
    -   **\<ReceiveLocationName\>.** The name of the receive location for which details will be displayed. If the receive location name contains spaces, enclose the name in quotes.  
  
    -   **/?.** Displays help.  
  
         For example (VBScript):  
  
        ```  
        cscript EnumRecLocs.vbs  
        ```  
  
         -OR- (Visual C#):  
  
        ```  
        EnumRl "My Receive Location #3"  
        ```  
  
         -OR- (Visual C#):  
  
        ```  
        EnumRl /?  
        ```  
  
    > [!NOTE]
    >  The VBScript version of this sample does not accept any command-line parameters, and therefore is only capable of retrieving and displaying details about all configured receive locations.  
  
## Comments  
 All tasks that you can perform in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console can also be performed by using script that accesses the Windows WMI object model and by using Visual C# that accesses the **System.Management** objects provided by the .NET Framework.  
  
 The script file EnumRecLocs.vbs and the Visual C# source file EnumRLs.cs contain detailed comments with further explanation about the operations that they perform. For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## See Also  
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)