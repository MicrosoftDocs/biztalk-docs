---
title: "WIP Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fc623fa-910a-4089-9c81-111402dad2fc
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuration for WIP
The TI Configuration Tool provides assistance in creating an app.config file for use with TI WIP applications. The app.config file can contain information about the TI WIP Objects and the Remote Environments to be used with the objects. The HIS 2016 SDK contains a WIP projected named ApplicationIntegrationStarterGuide with a readme file that steps through the process of creating an app.config file using the TI Configuration Tool.

> [!NOTE]
> It is recommended to run the TI Configuration Tool as a user that has read/write access to the file location where the config file is located.

## Nodes
* ### **Configuration Files**

    Right-click the Configuration Files node to display the following options:
  - **Open**. Opens an existing config file.

  - **New**. Creates a new config file.

  - **Import XML Configuration**. Imports XML generated from an older installation of Host Integration Server. This XML file is generated using the TI Manager on the older server.

  - **Expand All**. Expand all nodes on all open config files.

  - **Collapse All**. Collapse all nodes on all open config files.

    When a config file is open, the following nodes will be displayed:
  - [Common WIP and HIP Nodes:](../core/common-wip-and-hip-nodes.md)
      - AppFabric Cache Location
      - Configuration Read Order
      - Conversion Behavior
  - [Objects](../core/wipobjects.md)
  - [Remote Environments](../core/wipremoteenvs.md)
