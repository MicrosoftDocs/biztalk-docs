---
title: "Configuration for HIP | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 258750d9-18ce-4a1f-93ae-08347af3ab34
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuration for HIP
The TI Configuration Tool provides assistance in creating the HIPService.exe.config file that gives the HIP runtime engine the information necessary to read incoming data, process the data via a custom written component, and send back response data.  When run as an admin, the tool will also install the configured HIP Services and can be used to start and stop the HIP Services.  The TI Runtime uses the HIPService.exe.config file that resides in the %snaroot% directory.

> [!NOTE]
> It is recommended to run the TI Configuration Tool as a user that has read/write access to the file locations where the config files are located. When using HIP, the user should also have rights to start and stop Windows services.
 
## Nodes
* ### **Configuration Files**

    Right-click the Configuration Files node to display the following options:
  - **Open**. Opens an existing config file.
    
  - **New**. Creates a new config file.
    
  - **Import XML Configuration**. Imports XML generated from an older installation of Host Integration Server. This XML file is generated using the TI Manager on the older server.
    
  - **Expand All**. Expand all nodes on all open config files.
    
  - **Collapse All**. Collapse all nodes on all open config files.
    
    [!NOTE]When a config file is open, the following nodes will be displayed:
  - [Common WIP and HIP Nodes:](../core/common-wip-and-hip-nodes.md)
      - AppFabric Cache Location
      - Configuration Read Order
      - Conversion Behavior
  - [ESSO Security Policies](../core/esso-security-policies.md)
  - [Objects](../core/objects.md)
  - [Services](../core/services2.md)
  - [SNA Host Environments](../core/sna-host-environments.md)
  - [TCP Host Environments](../core/tcp-host-environments.md)
        
* ### **Installed Services**
    [!NOTE]Right-click the Installed Services node to display the following options:
  - **New...** Create a new HIP Service from the open HIPService.exe.config.
    
  - **Refresh**. Refresh the status of the listed HIP Services.
    
  - **Expand All**. Expand the list of the installed HIP Services.
    
  - **Collapse**. Collapse the list of the installed HIP Services.
   
    [!NOTE]When there are HIP Services installed, right-click on a service to display the following options:
    - **Start**. Start the service.
    - **Stop**.  Stop the service.
    - **Uninstall**. Uninstall the service.
    