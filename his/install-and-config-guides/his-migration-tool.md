---
title: HIS Migration Tool
description: Learn about the Host Integration Server (HIS) Migration Tool.
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 11/30/2017
---

# HIS Migration Tool

## Overview

The HIS Migration Tool assists with migrating to HIS 2016 from earlier versions of HIS as well as assisting with migrating the configuration from an existing HIS 2016 installation to another server. The migration tool will harvest the configuration information in an existing HIS installation and allow that information to be applied to a new installation of HIS 2016. The configuration information that is harvested includes HIS Services, Registry Entries, config files and SNA Gateway Configuration information.

- [Download the Host Integration Migration Tool](https://www.microsoft.com/en-us/download/details.aspx?id=105765) (HisMigration.exe).

## Tool Syntax

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

[Same Server Migration](../install-and-config-guides/same-server-migration.md)
[Server to Server Migration](../install-and-config-guides/server-to-server-migration.md)
