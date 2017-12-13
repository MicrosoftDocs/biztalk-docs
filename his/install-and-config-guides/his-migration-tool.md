---
title: "HIS Migration Tool | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b9417d4-2b91-4c2d-9d04-515556d59dd2
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HIS Migration Tool
## Overview
The HIS Migration Tool assists with migrating to HIS 2016 from earlier versions of HIS as well as assisting with migrating the configuration from an existing HIS 2016 installation to another server. The migration tool will harvest the configuration information in an existing HIS installation and allow that information to be applied to a new installation of HIS 2016. The configuration information that is harvested includes HIS Services, Registry Entries, config files and SNA Gateway Configuration information. 
    
Download the HIS Migration Tool (HisMigration.exe) from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=829851) (http://go.microsoft.com/fwlink/?linkid=829851).

## HIS Migration Tool Syntax
```
    HisMigration drive:path [/Apply | /Save] [/Overwrite] [/?]

    drive:path The full path to an existing directory.

    /Apply     Apply a previously saved configuration to the current version of HIS.
    
    /Overwrite Overwrite any existing files when doing a /Save.
               This entry is ignored when using /Apply.

    /Save      Save all HIS configuration information to the specified directory.
               If the directory is not empty, then /Overwrite must also be specified.
               This is the default if /Apply is not specified.

    /?         Displays this information.
```
## See Also
### [Same Server Migration](../install-and-config-guides/same-server-migration.md)
### [Server to Server Migration](../install-and-config-guides/server-to-server-migration.md)
