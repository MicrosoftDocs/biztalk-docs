---
description: Move to Host Integration Server 2020 from an older or previous version. Or, move an existing HIS 2020 configuration to another server.
title: HIS 2020 Migration Tool
ms.date: 04/16/2021
ms.service: host-integration-server
ms.topic: conceptual
---

# Host Integration Server migration tool

The Host Integration Server (HIS) Migration Tool:

- Helps move to HIS 2020 or HIS 2016 from earlier versions of Host Integration Server.
- Helps move the configuration from an existing HIS 2020 or HIS 2016 installation to another server.

The migration tool collects the configuration information in an existing HIS installation, and applies the information to a new installation. This configuration information includes the HIS services, registry entries, configuration files, and SNA Gateway configuration information.

- [Download the Host Integration Migration Tool](https://www.microsoft.com/download/details.aspx?id=54950) (HisMigration.exe).

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

## See also

[Same Server Migration](../install-and-config-guides/same-server-migration-2020.md)
[Server to Server Migration](../install-and-config-guides/server-to-server-migration-2020.md)
