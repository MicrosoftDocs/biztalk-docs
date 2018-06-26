---
title: "Using BizTalk Adapter Tracing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Adapter Trace Utility, installing"
  - "installing, Adapter Trace Utility"
  - "Adapter Trace Utility, enabling"
  - "Adapter Trace Utility, running"
  - "enabling, Adapter Trace Utility"
ms.assetid: ddc6b2c7-9dee-43c1-950b-8fd580bfcb26
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using BizTalk Adapter Tracing
This topic describes how to install the Trace Log tool and how to enable BizTalk adapter tracing.  
  
## Install the Trace Log Tool  
  
#### To install the Trace Log tool (tracelog.exe)  
  
1. Download the Trace Log tool from the [Microsoft® Windows® Software Development Kit Update for Windows Vista](http://go.microsoft.com/fwlink/?LinkId=128279) Web site.  
  
   > [!NOTE]
   >  Install this version (6.0) of the SDK even if you are running [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]. If you install the **Windows SDK for Windows Server 2008 and .NET Framework 3.5** version (v. 6.1), it will not install the Trace Log tool.  
  
2. Start the **Microsoft® Windows® Software Development Kit Update for Windows Vista** Web installation program by clicking the link for the **PSDK-x86.exe** file at the bottom of the Web page.  
  
   > [!NOTE]
   >  If you are using a 64-bit version of Windows choose the correct files to download for your system.  
  
3. In the **Select an Installation Type** dialog box, choose the option for a **Custom** installation, and then click **Next**.  
  
4. Accept the default installation location and then click **Next**.  
  
5. In the **Custom Installation** dialog box, click to clear all the available features.  
  
6. Expand the **Microsoft Windows Core SDK** feature, and then expand the **Tools** feature.  
  
7. Choose the **Tools (Intel 64-bit)** feature, and then click **Will be installed on local hard drive**.  
  
8. Click **Next**, and then click **Next** again to start the installation.  
  
   > [!NOTE]
   >  After installing the **Microsoft® Windows® Software Development Kit Update for Windows Vista** you may be prompted to reboot depending upon what other features you chose to install along with the Trace Log tool. This is because certain components of the **Microsoft® Windows® Software Development Kit Update for Windows Vista** will not function correctly until the reboot has been completed. You do not need to reboot to use the Trace Log tool.  
  
## Enable BizTalk Adapter Tracing with trace.cmd  
  
#### To enable BizTalk adapter tracing  
  
1. At a command prompt, change the current directory to the directory where BizTalk Server is installed. By default, BizTalk Server is installed in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] directory.  If using a 64-bit version of Windows and BizTalk Server, the installation path is [!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)].  
  
2. Type the following command, and then press ENTER:  
  
    **trace -tools "Path of the Trace Log tool"**  
  
    By default, the Trace Log tool (tracelog.exe) is located in the **C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin** directory. If using a 64-bit version of Windows the Trace Log tool is located at **C:\Program Files (x86)\Microsoft SDKs\Windows\v6.0\Bin**.  You must enclose the path of the Trace Log tool in quotation marks.  
  
    For example, type the following command, and then press ENTER:  
  
    **trace -tools "C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin"**  
  
   > [!NOTE]
   >  The **-tools** switch indicates to the Trace.cmd file the location of the Tracelog.exe file.  
   >   
   >  If the command successfully runs, the output will be like below:  
   >   
   >  **trace 2.0 - Manage BizTalk 2006 Release Bits Tracing.**  
   >   
   >  **Setting TRACE_TOOL_SEARCH_PATH to "C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin "**  
  
## Capture Trace output with trace.cmd  
  
#### To capture trace output  
  
1. At a command prompt, change the current directory to the directory where BizTalk Server is installed.  
  
2. At a command prompt, type the following command, and then press ENTER:  
  
    **trace -start**  
  
3. Reproduce the scenario for which you want to capture trace output.  
  
4. At a command prompt, type the following command, and then press ENTER:  
  
    **trace -stop**  
  
5. After you stop the trace, a binary file that is named **Btstrace.bin** is generated in the folder where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.  
  
6. Send the **Btstrace.bin** file to Microsoft Product Support Services for analysis.  
  
## See Also  
 [Using Adapters](../core/using-adapters.md)   
 [Troubleshooting the Windows SharePoint Services Adapter](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)