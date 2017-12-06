---
title: "Release Notes | Microsoft Docs"
ms.custom: ""
ms.date: "2016-10-24"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6bf8d13-ca71-411f-97e4-ef3ef18dae34
caps.latest.revision: 10
author: MandiOhlinger
manager: anneta
ms.author: "mandia"
---
# Release Notes
These release notes summarize the most important issues in [!INCLUDE[his2016](../install-and-config-guides/includes/his2016-md.md)].  
  
## Software  
 A single Microsoft Installer (MSI) file contains the server software. You can download the software from the [Microsoft TechNet evaluation center](http://go.microsoft.com/fwlink/p/?LinkId=808396) (http://go.microsoft.com/fwlink/p/?LinkId=808396).  
  
## Upgrade  
 You cannot do an in-place upgrade to HIS 2016.  You must uninstall all existing copies of Host Integration Server, and then install HIS 2016.  A migration tool is available to assist in upgrading from previous versions of HIS.  You can download the migration tool from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=829851) (http://go.microsoft.com/fwlink/?linkid=829851). For further information see [HIS Migration Tool](../install-and-config-guides/his-migration-tool.md).
  
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
 HIS 2016 includes technology for telemetry and error reporting. The HIS product team utilizes this data to improve the quality, reliability, and performance of [!INCLUDE[hisHostIntServNoVersion](../install-and-config-guides/includes/hishostintservnoversion-md.md)].  Ths includes:  
  
-   Installation and Configuration:  
  
    -   Installation monitors the features installed or removed.  
  
    -   Configuration monitors the features configured or unconfigured.  
  
-   Network Integration:  
  
    -   SNA Configuration monitors the the SNA services features configured or unconfigured.
    
    -   SNA Client monitors the the SNA client connections established by reporting the connection instance by type.

    -   SNA Sessions monitors the the SNA sessions connections established by reporting the session instance by type.

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
 HIS no longer includes on-the-box documentation. As a result, some links may not work correctly. Go to [Host Integration Server Core Documentation](../Topic/Host%20Integration%20Server%20Core%20Documentation.md) for information on network integration, message integration, and more.