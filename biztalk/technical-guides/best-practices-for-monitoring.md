---
title: "Best Practices for Monitoring | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5b180e2-bdd3-4081-9531-d96be7dabe1a
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Monitoring
This topic provides best practices for monitoring your Microsoft BizTalk Server environment and applications.  
  
 **Create and then implement a monitoring plan for your BizTalk applications and infrastructure**  
  
- Read the monitoring topics in this guide to ensure a more complete monitoring solution. Factors to consider include the following:  
  
  -   Who will perform the daily, weekly, monthly, and as needed monitoring tasks?  
  
  -   Is someone notified of events, suspended messages, or other system or application failures?  
  
  -   Are "expected" exceptions filtered or given a lower priority?  
  
  -   Are all host instances monitored to ensure they continue running?  
  
  -   Are all custom services, custom event logs, and custom databases monitored?  
  
  -   Are the SQL Server computers and the BizTalk Server SQL agent jobs monitored?  
  
  **If possible, install a monitoring application such as [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] in order to automate the monitoring of your BizTalk Server applications and infrastructure**  
  
- Using Microsoft System Center Operations Manager is the preferred approach for automated monitoring because the BizTalk Server management packs provide hundreds of built-in rules for BizTalk Server.  
  
   For more information, see the following resources:  
  
  -   [Microsoft BizTalk Server Management Pack for System Center Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=190339) (http://go.microsoft.com/fwlink/?LinkID=190339).  
  
  -   [How to Import a Management Pack in Operations Manager 2007](http://go.microsoft.com/fwlink/?LinkID=98348) (http://go.microsoft.com/fwlink/?LinkID=98348)  
  
  -   [How to Mark BizTalk Server Databases for Customized Monitoring](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
  **Run the BizTalk Server Best Practices Analyzer**  
  
- The BizTalk Server Best Practices Analyzer examines a BizTalk Server deployment and generates a list of issues pertaining to best practices standards. The tool performs configuration-level verification by gathering data from different information sources, such as Windows Management Instrumentation (WMI) classes, SQL Server databases, and registry entries. The data is then used to evaluate the deployment configuration. The tool reads and reports only and does not modify any system settings, and is not a self-tuning tool.  
  
   You can download the BizTalk Server Best Practices Analyzer at [http://go.microsoft.com/fwlink/?LinkId=83317](http://go.microsoft.com/fwlink/?LinkId=83317) (http://go.microsoft.com/fwlink/?LinkId=83317).  
  
  **Run the Performance Analysis of Logs tool (PAL)**  
  
- PAL is available as a free download at [https://github.com/clinthuffman/PAL](https://github.com/clinthuffman/PAL). For important installation information, see [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).  
  
  **Run Log Parser**  
  
- Log Parser is a powerful, versatile tool that provides universal query access to text-based data such as log files, XML files and CSV files, as well as key data sources on the Windows® operating system such as the Event Log, the Registry, the file system, and Active Directory®. You may want to use this tool to query a significant amount of logging information. You can download the Log Parser tool at [http://go.microsoft.com/fwlink/?LinkID=85574](http://go.microsoft.com/fwlink/?LinkID=85574)  
  
  **Run the BizTalk MsgBoxViewer Tool**  
  
  Run the [BizTalk MsgBoxViewer tool](http://go.microsoft.com/fwlink/?LinkId=151930) available from [http://go.microsoft.com/fwlink/?LinkId=151930](http://go.microsoft.com/fwlink/?LinkId=151930). This tool analyzes the BizTalk MessageBox and other databases and generates an HTML report containing warnings, if any, and other information related to the databases. You can also save the reports for later use. These reports might be useful when troubleshooting issues with the BizTalk application.  
  
  If the BizTalk MsgBoxViewer tool identifies any issues, run the [Terminator tool](http://go.microsoft.com/fwlink/?LinkId=151931) available at [http://go.microsoft.com/fwlink/?LinkId=151931](http://go.microsoft.com/fwlink/?LinkId=151931). This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool. For more information about how the Terminator tool integrates with the BizTalk MsgBoxViewer tool, see [Using BizTalk Terminator to resolve issues identified by BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932) (http://go.microsoft.com/fwlink/?LinkId=151932).  
  
> [!NOTE]  
>  Use of these tools is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of these programs. Use of these programs is entirely at your own risk.  
  
 **Make monitoring a priority**  
  
-   Consistent monitoring of BizTalk Server applications and infrastructure is essential to maintaining a healthy environment.  
  
-   Regularly evaluate and adjust your monitoring tools over time and as your BizTalk Server applications and infrastructure change.