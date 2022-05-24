---
title: Hardware and Software Requirements for BizTalk Server 2020 | Microsoft Docs
description: Describes the software prerequisites and supported version lists in order to install BizTalk Server 2020.
ms.custom: biztalk-2020
ms.prod: biztalk-server
ms.date: 04/07/2020
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: dougeby
---

# Hardware and Software Requirements for BizTalk Server 2020

## Hardware requirements

The following table lists the minimum hardware requirements for your BizTalk Server computer. In a production environment, the volume of traffic may require greater hardware requirements for your servers.

- **Computer and processor**: A computer with an Intel Pentium-compatible CPU that is:
  - 1.4 GHz or higher

  Hyper-threading and multi-core processors are supported.

  The 64-bit versions of BizTalk Server require a 64-bit operating system running on an x64-based system. Computers based on CPUs that are compatible with the AMD64 (x86-64) and Extended Memory 64-bit Technology (EM64T) processor architecture are considered x64-based systems.

  BizTalk Server is not supported on Itanium-based systems.

- **Memory**: 4 GB or more
- **Hard disk**: 10 GB of available hard disk space for a complete installation, including the operating system and all prerequisite software. The hard disk must be NTFS formatted.

> [!TIP]
> The hardware requirements listed are the minimum. Every environment is different and there's a very good chance that your environment may need more depending on your throughput requirement and load. See [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](https://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx). Also refer to Windows System requirements for [Windows Server 2016](/windows-server/get-started/system-requirements) and [Windows Server 2019](/windows-server/get-started-19/sys-reqs-19).

## Software requirements & supported versions

- **Microsoft Windows**: Required. Supported versions include:
  - Windows Server 2019
  - Windows Server 2016
  - Windows 10

- **Internet Information Services (IIS)**: Provides a scalable web application infrastructure, and is required for EDI, BAM, Management REST API, and the SharePoint adapter.

  IIS is included with the Windows operating system.

- **Windows Identity Foundation**: Optional. Used by the Windows SharePoint Services Client Side Object Model (CSOM), which is automatically installed when you install BizTalk Server.

  Windows Identity Foundation is included with the Windows operating system as a **Feature**.

- **Microsoft SharePoint**: Optional. If you plan to receive or send messages from SharePoint Services, then a SharePoint Services computer is required. It can be installed on the same computer as BizTalk Server, or preferably on a separate computer.

  Supported versions:

  - SharePoint Services 2019
  - SharePoint Services 2016
  - SharePoint Services Online

- **Microsoft Office**: Optional. Required by Business Activity Monitoring (BAM) to display a real-time view of business processes. 

  Supported versions:

  - Microsoft Office Excel 2019
  - Microsoft Office Excel 2016

  BizTalk Server supports only 32-bit versions of Office.

- **Microsoft .NET Framework**: Required for all BizTalk Server managed components. BizTalk projects created in Visual Studio require the Visual Studio build target be set to your .NET Framework version. 

  Supported minimum version:

  - .NET Framework 4.7.2

- **Microsoft Visual Studio**: Optional. Provides a development environment for building BizTalk Server applications. Required for BizTalk Server Developer Tools and SDK.

  Enterprise (recommended) and Professional editions are supported. Visual Studio Community Edition isn't supported.

  Supported minimum versions:

  - Visual Studio 2019 (Version 16.4.0)

- **Microsoft Visual C++ 2015-2019 Redistributable Package**: Required. The Microsoft Visual C++ Redistributable Package installs runtime components of Visual C++ Libraries required to run applications developed with Visual C++ on a computer that doesn't have Visual C++ installed.

  Supported versions:

  - The x86 and x64 versions are required. Download at [Visual C++ 2015-2019 Redistributable Package x86](https://aka.ms/vs/16/release/VC_redist.x86.exe) and [Visual C++ 2015-2019 Redistributable Package x64](https://aka.ms/vs/16/release/VC_redist.x64.exe).

- **Microsoft OLE DB Driver for SQL Server**: Required on all BizTalk Server devices.

  Supported minimum versions:

  - Microsoft OLE DB Driver 18.3.0 for SQL Server. Download at [Microsoft OLE DB Driver for SQL Server](/sql/connect/oledb/download-oledb-driver-for-sql-server?view=sql-server-ver15&preserve-view=true).

- **Microsoft SQL Server**: Required for BizTalk Server Runtime, EDI, and BAM. For optimal performance, Microsoft recommends the Enterprise Edition of SQL Server. Other considerations:

  - To use SQL Server AlwaysOn Availability Groups (AG), use SQL Server 2016 SP2 CU7 and newer versions. Starting with SQL Server 2016, AlwaysOn AG supports MSDTC; MSDTC is required by BizTalk.
  - BAM real-time aggregation (RTA) is not supported in the Standard Edition of SQL Server. To use BAM RTA, install SQL Server Enterprise Edition.
  - Using SQL Server Express Edition is not recommended. The Express edition does not include certain features needed by BizTalk Server.
  - BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations. Binary collations are not supported.

  Supported versions:

  - Microsoft SQL Server 2019
  - Microsoft SQL Server 2017
  - Microsoft SQL Server 2016 SP2 CU7

- **SSIS Catalog** (SSIDB): Optional. Required to use BAM. [Create the SSIS Catalog](/sql/integration-services/catalog/ssis-catalog#create-the-ssis-catalog).

- **SQL Server Database Mail**: Optional. Required to use BAM Alerts.

  SQL Server Database Mail is included with SQL Server.

- **SQL Server Analysis Services ADOMD.NET**: Optional. Required to use BAM Alerts.

  Supported versions:

  - SQL Server 2016 Analysis Services ADOMD.NET. Download at [SQL Server 2016 Feature Pack](https://www.microsoft.com/download/details.aspx?id=56833).

- **WinSCP**: Required to use the SFTP adapter.

  Supported versions:

  - WinSCP version 5.15.4. Download at [WinSCP](http://winscp.net).

- **MQSeries adapter**: Optional. Required only when using IBM WebSphere MQ.

  Supported versions:

  - IBM WebSphere MQ 8
  - IBM WebSphere MQ 9

- **LOB and enterprise systems**: Required when using the adapters in the BizTalk Adapter Pack. [BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md) lists the available system adapters.

  [Supported Line-of-Business (LOB) and Enterprise systems](../adapters-and-accelerators/lob-and-enterprise-2020-support.md)

## Service Pack and Cumulative Update Support

All service packs, cumulative updates, security updates, and hotfixes are supported on a BizTalk Server. It is strongly encouraged to install the latest update for Windows, SQL Server, Visual Studio, and any program installed. Service Packs for Microsoft products are supported based on the baseline support for that product. Refer to [Support Lifecycle Index](/lifecycle/) for BizTalk Server, SQL Server, Visual Studio, and other Microsoft programs.

[Service Pack and cumulative update list for BizTalk Server](https://support.microsoft.com/help/2555976)

## Next steps

[Set up and install prerequisites](../install-and-config-guides/set-up-and-install-prerequisites-for-biztalk-server-2020.md)