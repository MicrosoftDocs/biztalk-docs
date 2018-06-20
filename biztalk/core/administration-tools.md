---
title: "Administrative and performance tools | Microsoft Docs"
description: Common tools to manage tasks, performance, and tracing in BizTalk Server
ms.custom: ""
ms.date: "11/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 932814f7-2ab3-45cb-8bbc-eaf00fcb24a0
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Administrative and performance tools 

## Tools list
You can use the following tools to administer BizTalk ServerBizTalk Server, to manage BizTalk Server groups, to deploy BizTalk Server applications, to interact with trading partners, and to monitor the status of BizTalk Server:  
  
- **BizTalk Server Administration console**. The BizTalk Server Administration console is the primary management tool for BizTalk Server. It provides a graphical user interface for performing all of the deployment operations for a BizTalk application. For example, you can start the Import, Installation, and Export Wizards as well as add and remove an application's artifacts and make other modifications to the application.  
  
   Using the BizTalk Server Administration console, you can use view live or archived message event or service instance data to track the health of your BizTalk Server implementation, identify bottlenecks, and monitor the BizTalk Server environment. You can view the technical details of a particular orchestration, pipeline, or message instance, as well as see the message flow of a particular message that enters the system.  
  
   For information about using the BizTalk Server Administration console, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).  
  
- **BTSTask command-line tool**. BTSTask enables you to perform many administrative tasks from the command line. For more information about using BTSTask, see [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md).  
  
- **Scripting and programmability APIs**. You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
   The WMI object model exposes and simplifies administrative APIs. All administration APIs expose some form of the following operations on every object they manage: create, enumerate, modify, and delete. WMI exposes this functionality in a consistent manner for all WMI objects.  
  
- **Business Activity Monitoring (BAM).** BAM uses a Microsoft Office Excel workbook to provide business users with a way to see a real-time holistic view of business processes. For more information about BAM, see [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md).  


- [**BizTalk Health Monitor**](http://blogs.msdn.com/b/biztalkhealthmonitor/ "BizTalk Health Monitor ") was created by the BizTalk support team to collect information about a BizTalk environment, including table usage and known issues. An report is generated with potential problem areas highlighted. Consider executing this tool and reviewing the output on a regular basis to help maintain your BizTalk environment. This replaces BizTalk MsbBox Viewer.

- [**BizTalk Terminator Tool**](https://www.microsoft.com/download/en/details.aspx?id=2846 "BizTalk Terminator Tool") was created by the BizTalk support team to resolve common database integrity issues typically found in the BizTalk MsgBox Viewer output. Common tasks include removing instances and purging large tables. For more information about the BizTalk Terminator tool, go to [this post](http://blogs.msdn.com/b/biztalkcpr/archive/2011/02/10/using-biztalk-terminator-to-resolve-issues-identified-by-biztalk-msgboxviewer.aspx) in One Blog for BizTalk Engineers.

- [**Microsoft BizTalk LoadGen 2007**](https://www.microsoft.com/download/details.aspx?id=14925) generates message transmission loads to run performance and stress tests for your Microsoft BizTalk Server applications, and provides performance counters to monitor the performance of the infrastructure running BizTalk Server.

- [**BizTalk Server Best Practices Analyzer**](https://www.microsoft.com/downloads/details.aspx?FamilyID=93d432fe-1370-4b6d-aaa8-a0c43c30f5ab "BizTalk Server Best Practices Analyzer") performs configuration-level verification by reading and reporting only. The Best Practices Analyzer gathers data from different information sources, such as Windows Management Instrumentation (WMI) classes, SQL Server databases, and registry entries. The Best Practices Analyzer uses the data to evaluate the deployment configuration. The Best Practices Analyzer does not modify any system settings, and is not a self-tuning tool.

- [**Performance Analysis of Logs (PAL)**](https://github.com/clinthuffman/PAL) is a powerful tool that reads in a performance monitor counter log (any known format) and analyzes it using complex, but known thresholds (provided). The tool generates an HTML based report which graphically charts important performance counters and throws alerts when thresholds are exceeded.

- [**DebugView for Windows**](https://docs.microsoft.com/sysinternals/downloads/debugview) is an application that lets you monitor debug output on your local system, or any computer on the network that you can reach via TCP/IP. It is capable of displaying both kernel-mode and Win32 debug output, so you don't need a debugger to catch the debug output your applications or device drivers generate, nor do you need to modify your applications or drivers to use non-standard debug output APIs.

- [**Log Parser 2.2**](https://www.microsoft.com/download/details.aspx?id=24659) is a powerful, versatile tool that provides universal query access to text-based data such as log files, XML files and CSV files, as well as key data sources on the Windows operating system such as the Event Log, the Registry, the file system, and Active Directory.

- [**Process Explorer**](https://docs.microsoft.com/sysinternals/downloads/process-explorer) is useful for tracking down DLL-version problems or handle leaks, and provide insight into the way Windows and applications work.

- [**TCP Trace**](http://www.pocketsoap.com/tcptrace/ "TCP Trace") is used to monitor text based network traffic between client and server. Useful while using adapters like SOAP,HTTP,POP3 etc to see the message travelling via the wire.

- [**DTCPing**](https://www.microsoft.com/download/details.aspx?id=2868) is designed to assist with troubleshooting Microsoft DTC Firewall Issues, which you'll often see in a multiserver BizTalk deployment.

  
## See Also  
 [Application Deployment and Management Tools](../core/application-deployment-and-management-tools.md)