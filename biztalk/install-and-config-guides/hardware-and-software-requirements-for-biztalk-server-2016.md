---
title: "Hardware and Software Requirements for BizTalk Server 2016 | Microsoft Docs"
ms.custom: ""
ms.prod: biztalk-server
ms.date: "06/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6120afd-310e-4155-8c23-aadb5b9a1a35
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Hardware and Software Requirements for BizTalk Server 2016

## Hardware requirements
The following table lists the minimum hardware requirements for your BizTalk Server computer. In a production environment, the volume of traffic may require greater hardware requirements for your servers. 

| Resource	|Minimum Requirement |
| --- | --- |
|Computer and processor	| A computer with an Intel Pentium-compatible CPU that is: <ul><li>1 GHz or higher for single processors</li><li>900 MHz or higher for double processors</li><li>700 MHz or higher for quad processors</li></ul> **NOTE**: Hyper-threading and dual-core processors are supported.<br/><br/>The 64-bit versions of BizTalk Server require a 64-bit operating system running on an x64-based system. Computers based on CPUs that are compatible with the AMD64 (x86-64) and Extended Memory 64-bit Technology (EM64T) processor architecture are considered x64-based systems.<br/><br/>BizTalk Server is not supported on Itanium-based systems. |
|Memory	| 2 GB or more|
|Hard disk	|10 GB of available hard disk space for a complete installation, including the operating system and all prerequisite software. The hard disk must be NTFS formatted.|

> [!TIP] 
> The hardware requirements listed are the minimum. Every environment is different and there's a very good chance that your environment may need more. See [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx). 


## Software Requirements

| Software  | 	Versions | 	Required for | 
| --- | --- | --- | 
| Microsoft Windows	| <ul><li>Windows Server 2016</li><li>Windows Server 2012 R2</li><li>Windows 10</li><li>Windows 8.1	</li></ul> | | 
| Internet Information Services (IIS)	| The version that comes with the operating system.<br/><br/> [KB 224609](https://support.microsoft.com/kb/224609) lists the IIS versions. | Provides a scalable web application infrastructure, and is required for EDI, BAM, and the SharePoint adapter. |
| Windows Identity Foundation | Included with the operating system as a **Feature**. | Optional. <br/><br/>Used by the Windows SharePoint Services Client Side Object Model (CSOM), which is automatically installed when you install BizTalk Server. | 
| Microsoft SharePoint	| <ul><li>SharePoint Services 2016</li><li>SharePoint Services 2013 SP1</li><li>SharePoint Services Online</li></ul>  | Optional. <br/><br/>If you plan to receive or send messages from SharePoint Services, then a SharePoint Services computer is required. It can be installed on the same computer as BizTalk Server, or preferably on a separate computer. |
| Microsoft Office	| <ul><li>Microsoft Office Excel 2016</li><li>Microsoft Office Excel 2013</li></ul>**NOTE**: BizTalk Server supports only 32-bit versions of Office.  | Optional. <br/><br/>Required by Business Activity Monitoring (BAM) to display a real-time view of business processes. | 
| Microsoft .NET Framework	| <ul><li>.NET Framework 4.7 (Starting with [CU2](https://support.microsoft.com/kb/4021095))</li><li>.NET Framework 4.6.*x* </li></ul>**NOTE**: BizTalk projects created in Visual Studio require the Visual Studio build target be set to your .NET Framework version. | Required for all BizTalk Server managed components. | 
| Microsoft Visual Studio |Visual Studio 2015 | Optional. <br/><br/>Provides a development environment for building BizTalk Server applications. Ultimate Edition is recommended, but Premium and Professional are also supported. Required for BizTalk Server Developer Tools and SDK. |
| Microsoft Visual C++ 2013 Redistributable Package	| The x86 and x64 versions are required. Download at [Visual C++ Redistributable Packages for Visual Studio 2013](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package).	| Required.<br/><br/>The Microsoft Visual C++ Redistributable Package installs runtime components of Visual C++ Libraries required to run applications developed with Visual C++ on a computer that does not have Visual C++ installed.<br/><br/>**Note**: <br/> The 2013 version is required, even though Visual Studio 2015 is used.|
| Microsoft SQL Server	| <ul><li>Microsoft SQL Server 2016</li><li>Microsoft SQL Server 2014 SP1</li></ul> | Required for BizTalk Server Runtime, EDI, and BAM. <br/><br/>For optimal performance, Microsoft recommends the Enterprise Edition of SQL Server. To fully use the BizTalk Server SDK, or deploy BizTalk Server applications from Visual Studio, install the SQL Server Development Tools. <br/><br/>Other considerations: <ul><li>To use SQL Server AlwaysOn Availability Groups (AG), use SQL Server 2016 and newer versions. Only SQL Server 2016 AlwaysOn AG supports MSDTC; MSDTC is required by BizTalk. </li><li>BAM real-time aggregation (RTA) is not supported in the Standard Edition of SQL Server. To use BAM RTA, install SQL Server Enterprise Edition.</li><li>Using SQL Server Express Edition is not recommended. The Express edition does not include certain features needed by BizTalk Server.</li><li>BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations. Binary collations are not supported.</li></ul> |  |
| SQL Server Database Mail	| The version that comes with SQL Server. [Configure SQL Server Database Mail](https://msdn.microsoft.com/library/hh245116(v=sql.130).aspx).| Optional. <br/><br/>Required to use BAM Alerts. | 
| SQL XML | SQL XML 4.0 with Service Pack 1. [Download SqlXml 4.0 Service Pack 1 (SP1)](https://www.microsoft.com/en-us/download/details.aspx?id=30403). | Required for BizTalk Server Runtime, Administrative Tools, and BAM. <br/><br/> SQLXML enables XML support for your SQL Server Database. It allows developers to bridge the gap between XML and relational data. You can create XML view of your existing relational data, and work with the view as if it was an XML file. <br/><br/>**Note**: <br/>The redistributable CAB file automatically installs this for you. SQL XML may have its own software requirements (such as `.NET Framework 3.5` and `.NET Framework 2.0`), which are not included in the CAB file. If the BizTalk Server has internet access, the SQL XML software requirements may automatically install. If the BizTalk Server does not have internet access, then manually install the SQL XML software requirements.| 
| WinSCP | WinSCP version 5.7.7. [Download WinSCP](http://winscp.net).| Required to use the SFTP adapter. |

## Service Pack and Cumulative Update Support

All service packs, cumulative updates, security updates, and hot fixes are supported on a BizTalk Server. It is strongly encouraged to install the latest update for Windows, SQL Server, Visual Studio, and any program installed. Service Packs for Microsoft products are supported based on the baseline support for that product. Refer to [Support Lifecycle Index](http://go.microsoft.com/fwlink/p/?LinkID=151890) for BizTalk Server, SQL Server, Visual Studio, and other Microsoft programs.

[Service Pack and cumulative update list for BizTalk Server](https://support.microsoft.com/help/2555976)

 ## Next Step
 
 [Set up and install prerequisites](../install-and-config-guides/set-up-and-install-prerequisites-for-biztalk-server-2016.md)
