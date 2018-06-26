---
title: "Windows PowerShell and WMI Provider for HIS2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba4b6249-c13b-4975-833d-e3c01e2a5027
caps.latest.revision: 8
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Windows PowerShell and WMI Provider for HIS
Windows PowerShell is a task-based command-line shell and scripting language that you can use to administer client and server computers that are running Windows operating systems. Built on the .NET Framework, Windows PowerShell enables you to control and automate the administration of Host Integration Server, through the Host Integration Server Windows Management Interface (WMI) provider. The SNA Administration PowerShell samples illustrate how you use PowerShell to administer common objects in an Host Integration Server SNA Services configuration, including viewing the configuration of SNA Services, TN3270 and TN520 Services, and Host Print Services  
  
 **Location in the SDK**  
  
 \<installation directory>\Program Files\\Host Integration Server\SDK\Samples\NetworkIntegration\Administration\PowerShellScripts  
  
## File Inventory  
 The following table lists the files available to you and a description of each file.  
  
|**File(s)**|**Description**|  
|-------------------|---------------------|  
|displayHIS3270LUs.PS1|The displayHIS3270LUs.ps1 PowerShell script demonstrates how to enumerate and display information about the HIS 3270 LUs on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|displayHISIPDLCConnections.PS1|The displayHISIPDLCConnections.ps1 PowerShell script demonstrates how to enumerate and display IP-DLC Connection information on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|displayHISLUs.PS1|The displayHISLUs.ps1 PowerShell script demonstrates how to enumerate and display 3270 Display Logical Unit (LU) information on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|displayHISSDLCConnections.PS1|The displayHISSDLCConnections.ps1 PowerShell script demonstrates how to enumerate and display SDLC Connection information on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|displayHISSNADomains.PS1|The displayHISSNADomains.ps1 PowerShell script demonstrates how to enumerate and display SNA Domain information on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|displayHISSNAServices.PS1|The displayHISSNAServices.ps1 PowerShell script demonstrates how to enumerate and display SNA Services information on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|displayHISTN3270Services.PS1|The displayHISTN3270Services.ps1 PowerShell script shows how to enumerate and display TN3270 Service information on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|displayHISTN5250Services.PS1|The displayTNHIS5250Services.ps1 PowerShell script demonstrates how to enumerate and display TN5250 Service information on an Host Integration Server server computer by using the WMI Provider for HIS.|  
|HISSNAServiceController.PS1|The HISSNAServiceController PowerShell script demonstrates how to Start, Stop, and Pause the SNA Service for a computer by using the WMI interface provided by HIS.|  
|ModifyHIS3270LUproperties|The ModifyHIS3270LUproperties PowerShell script demonstrates how to modify HIS 3270 LU properties on an Host Integration Server server computer by using the WMI Provider for HIS.|  
  
 **How to Start Windows PowerShell with the Import System Modules Task**  
  
 In Windows 7 and Windows Server 2012, you can start a Windows PowerShell session that includes commands from all modules in your %Windir%\System32\WindowsPowerShell\1.0\Modules directory. The session also runs with the privileges of your Administrator account (the Run as administrator option.  
  
 For more information about Windows PowerShell modules and snap-ins, see Using Modules and Snap-Ins, How to Import a Module, and about_Modules in MSDN.  
  
 **To start Windows PowerShell ISE**  
  
 To start Windows PowerShell Integrated Scripting Environment (ISE), with the Import System Modules task, use the following procedure:  
  
- In Windows Vista, Windows Server 2008, and later versions of Windows, from the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click the **Windows PowerShell ISE** item.  
  
  **To open and run sample scripts**  
  
  To open and run an existing Host Integration Server sample script, use the following procedures:  
  
- On the toolbar, click **Open…**, or on the **File** menu, click **Open**.  
  
- In the **Open** dialog box, select the file that you want to open. The opened file appears in a new tab.  
  
- On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.  
  
  The **Output Pane** displays the results of the commands and scripts that you have run.  
  
> [!NOTE]
>  You may need to enable scripting on your computer. For information about PowerShell security, see Examining the Execution Policy at http://msdn.microsoft.com/library/bb648601(VS.85).aspx.  
  
 **Other Resources**  
  
For more information about Windows PowerShell 2.0, see the Windows PowerShell Getting Started Guide at http://msdn.microsoft.com/library/aa973757(VS.85).aspx.