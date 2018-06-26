---
title: "64-bit support overview for BizTalk Server | Microsoft Docs"
description: 64-bit support in adapters, processes, BizTalk Administration, BAM Tools, assemblies, orchestrations, and more in BizTalk Server
ms.custom: ""
ms.date: "09/27/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52ae9037-a7af-48e4-b6a3-bff7600802de
caps.latest.revision: 42
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server 64-Bit Support
This topic answers some frequently asked questions about 64-bit support for Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## Which versions of 64-bit Windows are supported?  
 All editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] support 32-bit execution and native 64-bit execution on the supported operating systems. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes 32-bit and 64-bit configuration options. 
 
  [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
  
 [Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)  
  
## Is there an extra cost for 64-bit support?  
 No. 64-bit support is included at no extra charge.  
  
## Is Itanium-based hardware supported?  
 For the BizTalk runtime, no. For BizTalk databases, yes.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires CPU hardware that supports AMD64 or EM64T. As a result, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is not supported on Windows running on Itanium-based 64-bit CPUs. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does support running with an Itanium-based [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Thus, all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are supported on Itanium 64-bit CPUs.  
  
## Which BizTalk Server processes run in 64-bit mode?  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] executables are hosted inside several different server runtimes. The following table lists which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes run in 64-bit mode.  
  
|Process|32-bit support|64-bit support|  
|-------------|---------------------|---------------------|  
|HTTP-based adapters (IIS)|Yes|Partial|  
|BizTalk Host instances|Yes|Yes|  
|Enterprise SSO|Yes|Yes|  
|BAM portal (IIS)|Yes|No|  
|SQL Server|Yes|Yes|  
  
##### HTTP-based adapters (IIS)  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components such as the HTTP, and SOAP adapters are hosted and executed inside Internet Information Services (IIS). All adapters are supported in 32-bit IIS mode. Some adapters support running in 64-bit IIS mode. For a complete list of 64-bit adapters, see the list of adapters later in this topic.  
  
##### BizTalk Host instances  
 A BizTalk Host is a logical group of servers, each one called a host instance. Each host instance is deployed as an NT service based on BTSNTSvc.exe. Orchestrations and in-process adapters are loaded and executed in host instances. Host instances can be configured to run in either 32-bit or 64-bit mode by using the **32-bit only** check box option in the **Host Properties** dialog box in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
##### Enterprise SSO  
 Microsoft Enterprise Single Sign-On (SSO) is run in a dedicated NT service (ENTSSO.exe). It is native 32-bit on 32-bit [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] and native 64-bit on 64-bit [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)].  
  
##### BAM portal (IIS)  
 Business Activity Monitoring (BAM) portal components must run in IIS using 32-bit ASP.NET 3.5. BAM Portal will run on 64-bit hardware in WOW mode. See "Running the BAM portal in a 64-bit environment" in [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md).  
  
##### SQL Server  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] communicates to Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] over native transport protocols that are interoperable between 32-bit and 64-bit versions of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Therefore, 32-bit and 64-bit [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] executables can communicate with either 32-bit or 64-bit versions of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. All [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stored procedures are supported in either 32-bit or 64-bit [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
## What about 32-bit/64-bit support in non-server processes?  
 **Microsoft Visual Studio**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] designer executables are hosted inside the 32-bit [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] supports development of 64-bit projects using the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], which can be deployed into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **Microsoft Management Console (MMC)**  
  
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console runs only as a 32-bit Microsoft Management Console (MMC) application, even on 64-bit [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]. Enterprise SSO supports both 32-bit and 64-bit MMC.  
  
 **Internet Explorer**  
  
 The BAM client requires 32-bit Internet Explorer to be installed and used on 64-bit [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)].  
  
## How do I enable native 64-bit execution of orchestrations?  
 Assign the orchestration to run in a host instance that has the **32-bit only** property not selected. The host instance must be running on a Windows x64 machine.  
  
## Can I build .NET assemblies that run in 64-bit orchestrations?  
 Yes. Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] developer can create assemblies that support 64-bit execution. These can be deployed with orchestrations and run in host instances configured for native 64-bit execution.  
  
## Will .NET Framework 2.0-compiled assemblies JIT-compile properly in both 32-bit and 64-bit?  
 Yes. If the assembly was compiled with the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 2.0 and the **AnyCPU** flag, a single DLL will JIT-compile properly in either 32-bit or 64-bit CLRs.  
  
## Can I install both 32-bit and 64-bit components in a single BizTalk MSI package?  
 Yes. An administrator can create an MSI package file from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application. The MSI file can contain both 32-bit and 64-bit DLLs and EXEs that were added to the BizTalk application. On 32-bit Windows, only the 32-bit DLLs and EXEs will be installed. On [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] x64, both 32-bit and 64-bit DLLs and EXEs will be installed.  
  
## How do 32-bit BizTalk Server executables run on Windows x64?  
 Windows x64 provides the ability to run both 32-bit and 64-bit executables on the same computer. 32-bit executables use the WOW64 service to emulate a 32-bit runtime environment.  
  
## Will 32-bit BizTalk Server executables have 4GB of addressable process memory on Windows x64?  
 Yes. On [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] x64, 32-bit BTSNTSVC and IIS processes are run under WOW64 and may utilize the full 4GB of virtual memory. This is an improvement over the default 2GB of addressable virtual memory on 32-bit Windows.  
  
 You can set the memory throttling threshold in percent (%) available, or in an absolute value. For example:  
  
-   If you use percent available (0-100), then the value you enter is a percentage of 2048 MB.  
  
-   If you use an absolute value, then the value you enter can be any value in MB up to 4096 MB (32-bit limit). On 64-bit hosts, you can specify a higher value up to theoretical 64-bit address limit of 2 TB.  
  
## Which adapters are capable of running in 64-bit mode?  
 By default, all adapters can run in 32-bit mode on 32-bit [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] and on WOW64 on 64-bit [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]. The following adapters can run in native 64-bit mode (in either IIS or BTSNTSVC as the host process):  
  
-   File  
  
-   HTTP  
  
-   MSMQ  
  
-   MQSeries  
  
-   SFTP  
  
-   SMTP  
  
-   SOAP  
  
-   WCF  
  
> [!NOTE]
>  The MQSeries adapter is supported in both 32-bit and 64-bit processes. The adapter has a MQSeries Agent that runs on IBM WebSphere MQ Server on Windows. [Prepare Your Computer for Installation](../install-and-config-guides/prepare-your-computer-for-installation.md) lists the MQ requirements.  
> 
> [!NOTE]
>  If your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications connect to a Windows Server 2003 computer (like SSO, SQL adapter, MQSeries, MQSAgent, Oracle, and so on), then install [934016](http://support.microsoft.com/kb/934016) and [934849](http://support.microsoft.com/kb/934849) on these Windows Server 2003 servers.  
> 
> [!NOTE]
>  Running the FTP adapter, POP3 adapter, and MIME Decoder on 64-bit host instances is not supported.  
  
## Are persisted BizTalk orchestrations dependent on 32-bit or 64-bit runtimes?  
 No. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] persists runtime components using formats that are independent of 32-bit or 64-bit runtimes. This includes orchestrations, messages, and ports. This persistence model enables an administrator to switch the host configuration between 32-bit and 64-bit without creating incompatibilities in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] data.  
  
## When I upgrade to BizTalk Server, will my BizTalk hosts run as 64-bit by default?  
 No. By default, upgrades to BizTalk Server mark all BizTalk host instances as 32-bit only. An administrator must create new host instances on Windows x64 computers and configure applications to use them.  
  
## Can I have a “mixed” BizTalk Server group that includes both 32-bit and 64-bit BizTalk runtimes?  
 Yes.  
  
## What languages are supported on 64-bit runtimes?  
 All supported languages are supported on both 32-bit and 64-bit runtimes.  
  
## What 64-bit SQL Server components are required to configure BAM tools?  
 The configuration wizard is a 32-bit process; therefore it requires certain components which allow it to communicate with 64-bit [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. You must install the following [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] client components to enable configuration of BAM tools:  
  
-   Connectivity Components  
  
-   Management Tools  
  
-   Legacy Components  
  
## See Also  
 [Performance and Capacity Planning](../core/performance-and-capacity-planning.md)
