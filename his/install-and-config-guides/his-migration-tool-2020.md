---
title: "HIS Migration Tool | Microsoft Docs"
description: Move to Host Integration Server 2020 from an older or previous version. Or, move an existing HIS 2020 configuration to another server.
ms.custom: ""
ms.date: "5/13/2020"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b9417d4-2b91-4c2d-9d04-515556d59dd2
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "dougeby"
---

# Host Integration Server migration tool

The Host Integration Server (HIS) Migration Tool:

- Helps move to HIS 2020 or HIS 2016 from earlier versions of Host Integration Server.
- Helps move the configuration from an existing HIS 2020 or HIS 2016 installation to another server.

The migration tool collects the configuration information in an existing HIS installation, and applies the information to a new installation. This configuration information includes the HIS services, registry entries, configuration files, and SNA Gateway configuration information.

[Download the HIS Migration Tool](https://go.microsoft.com/fwlink/?linkid=829851) (HisMigration.exe).

## Tool syntax

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

[Same Server Migration](../install-and-config-guides/same-server-migration-2020.md)
[Server to Server Migration](../install-and-config-guides/server-to-server-migration-2020.md)
