---
description: "Learn about the most important issues in Microsoft Host Integration Server (HIS) 2016."
title: "Release Notes | Microsoft Docs"
ms.custom: ""
ms.date: 10/24/2016
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6bf8d13-ca71-411f-97e4-ef3ef18dae34
caps.latest.revision: 11
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Release Notes

These release notes summarize the most important issues in [!INCLUDE[his2016](../includes/his2016-md.md)].  
  
## Software  
 A single Microsoft Installer (MSI) file contains the server software. You can download the software from the [Microsoft TechNet evaluation center](https://www.microsoft.com/evalcenter/evaluate-host-integration-server-2016).  
  
## Upgrade  
 You cannot do an in-place upgrade to HIS 2016.  You must uninstall all existing copies of Host Integration Server, and then install HIS 2016.  A [HIS migration tool](https://www.microsoft.com/download/details.aspx?id=54950) is available to assist in upgrading from previous versions of HIS. [HIS Migration Tool](../install-and-config-guides/his-migration-tool.md) has more details.
  
## Installation  
 The setup installation is a new simple wizard that installs the software, and also has an optional advanced dialog to select (install) or de-select (uninstall) features.  
  
## Configuration  
 The post-installation configuration is a new set of simple dialogs that configure the features, and also has advanced settings to (enable) or un-configure (disable) sub-features.  
  
 Configuration is required to use most features, including services, adapters, and tools.  
  
## 32-bit and 64-bit  
 You cannot install HIS 2016 on a 32-bit x86 only operating system. The setup installation supports 64-bit x64 operating systems. It installs features and tools to use side-by-side on x64 and x86 systems. For example, set up the installation and configuration so that you enable BizTalk Adapters to run in both a BizTalk Server 64-bit and 32-bit host application.  
  
## Client  
 The setup installation installs the server side-by-side with the client. The installation does not provide the client as a stand-alone option. The HIS team is developing a client-only MSI for x86 and x64 operating systems, which will be available at retail release.  
  
## Telemetry  
 HIS 2016 includes technology for telemetry and error reporting. The HIS product team utilizes this data to improve the quality, reliability, and performance of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  Ths includes:  
  
-   Installation and Configuration:  
  
    -   Installation monitors the features installed or removed.  
  
    -   Configuration monitors the features configured or unconfigured.  
  
-   Network Integration:  
  
    -   SNA Configuration monitors the SNA services features configured or unconfigured.
    
    -   SNA Client monitors the SNA client connections established by reporting the connection instance by type.

    -   SNA Sessions monitors the SNA sessions connections established by reporting the session instance by type.

    -   Session Integrator monitors the connections established by reporting the connection instance by type.
    
    -   TN3270 Emulator monitors the connections established by reporting the connection instance by type.  
  
-   Application Integration:  
  
    -   Transaction Integrator monitors the connections established by reporting the connection instance by type and programming model.  
  
-   Message Integration:  
  
    -   MQ Client monitors the connections established by reporting the connection instance by type.  
  
-   Data Integration:  
  
    -   DRDA Service monitors the connections established by reporting the connection instance by DRDA client class and version.  
  
    -   DRDA Service monitors the exceptions by reporting the instance based on SQLSTATE, SQLCODE, and reason code.    
    -   DRDA Clients for DB2 and Informix monitor the connections established by reporting the connection instance by DRDA server class and version, data provider name and data consumer process name.  
  
    -   DRDA Clients for DB2 and Informix monitors the exceptions by reporting the instance based on SQLSTATE, SQLCODE, and reason code.  
  
## Documentation  
 HIS no longer includes on-the-box documentation. As a result, some links may not work correctly. Go to [Host Integration Server Core Documentation](../core/host-integration-server-core-documentation.md) for information on network integration, message integration, and more.
