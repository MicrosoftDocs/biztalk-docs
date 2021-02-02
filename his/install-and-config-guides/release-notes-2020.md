---
description: "Learn more about: Release Notes"
title: "Release Notes | Microsoft Docs"
ms.custom: ""
ms.date: "5/13/2020"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6bf8d13-ca71-411f-97e4-ef3ef18dae34
caps.latest.revision: 11
author: "gplarsen"
ms.author: "hisdocs"
manager: "dougeby"
---

# Release Notes

These release notes summarize the most important issues in Host Integration Server 2020.  
  
## Software  

A single Microsoft Installer (MSI) file includes the server software. You can download the software from the [Microsoft Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-host-integration-server-2020).  
  
## Upgrade  

This release allows an in-place upgrade of HIS 2016. For versions older than HIS 2016, there's a [HIS migration tool](https://www.microsoft.com/download/details.aspx?id=54950) that can help upgrade from previous versionsS. For more information, see the [HIS migration tool](../install-and-config-guides/his-migration-tool-2020.md).

 After an in-place upgrade from HIS 2016 to HIS 2020, if the configuration tool is not allowed to open at the end of setup, the services may fail to start.   Many of the services depend on having the correct versions of the Visual C++ Runtime DLLs.  These are installed by the configuration tool when it first starts.  To fix this issue, simply launch the configuration tool from the Start menu.
  
## Installation  

The installation is a simple wizard that installs the software, and has an optional advanced dialog to select (install) or de-select (uninstall) features.  
  
## Configuration  

The post-installation configuration is a set of simple dialogs that configure the features, and has advanced settings to (enable) or un-configure (disable) sub-features. Configuration is required to use most features, including services, adapters, and tools.  
  
## 32-bit and 64-bit  

You can't install HIS 2020 Server on a 32-bit x86 operating system. The installation only supports 64-bit x64 operating systems. The server installs side-by-side support for most 32-bit applications. For example, the installation supports running a 32-bit APPC application or 32-bit emulator.   
  
## Client  

The 64-bit and 32-bit client installations are available as separate MSI packages.  
  
## Telemetry  

HIS 2020 includes technology for telemetry and error reporting. The HIS product team utilizes this data to improve the quality, reliability, and performance of Host Integration Server. This includes:  
  
- Installation and Configuration:  
  - Installation monitors the features installed or removed.  
  - Configuration monitors the features configured or unconfigured.  
  
- Network Integration:  
  
  - SNA Configuration monitors the SNA services features configured or unconfigured.
  - SNA Client monitors the SNA client connections established by reporting the connection instance by type.
  - SNA Sessions monitors the SNA sessions connections established by reporting the session instance by type.
  - Session Integrator monitors the connections established by reporting the connection instance by type.
  - TN3270 Emulator monitors the connections established by reporting the connection instance by type.  
  
- Application Integration:  
  - Transaction Integrator monitors the connections established by reporting the connection instance by type and programming model.  
  
- Message Integration:  
  - MQ Client monitors the connections established by reporting the connection instance by type.  
  
- Data Integration:  
  - DRDA Service monitors the connections established by reporting the connection instance by DRDA client class and version.  
  - DRDA Service monitors the exceptions by reporting the instance based on SQLSTATE, SQLCODE, and reason code.    
  - DRDA Clients for DB2 and Informix monitor the connections established by reporting the connection instance by DRDA server class and version, data provider name and data consumer process name.   
  - DRDA Clients for DB2 and Informix monitors the exceptions by reporting the instance based on SQLSTATE, SQLCODE, and reason code.  
  
## Documentation  

HIS no longer includes on-the-box documentation. As a result, some links may not work correctly. Go to [Host Integration Server Core Documentation](../core/host-integration-server-core-documentation.md) for information on network integration, message integration, and more.

## Next steps

See the [system requirements](system-requirements-2020.md).
