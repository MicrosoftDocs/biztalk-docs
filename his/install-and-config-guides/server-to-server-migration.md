---
description: "Learn more about: Server to Server Migration"
title: "Server to Server Migration"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Server to Server Migration

## Overview

The HIS Migration tool can be used for migrating the configuration from older versions of Host Integration Server to a new Host Integration Server 2016 Server or for migrating the configuration from one Host Integration Server 2016 Server to a different Host Integration Server 2016 Server.

## Steps to migrate from Host Integration Server on one server to Host Integration Server 2016 on a different server

- These instructions assume the migration tool is downloaded to a local C:\Files directory.
- On the first Host Integration Server, open an Administrative Windows Command Prompt and issue the following command:

    C:\Files>**HisMigration.exe C:\Files\HIS_Migrate /Save**

    > [!NOTE]
    > C:\Files\HIS_Migrate must exist and have no files in it

- On the new Host Integration Server 2016 Server - copy the C:\Files directory and subdirectory from the first HIS Server.
- The C:\Files\HIS_Migrate\System\Config\com.cfg file must be modified using the snacfg.exe tool. First generate a command file using the /print option, edit the command file to change the server name from the existing server name to the new server name, then use the snacfg.exe tool with the new command file to generate a new com.cfg file.

    1. SNACFG.exe #C:\Files\HIS_Migrate\System\Config\com.cfg /print > HISconfig.txt
    2. Make a copy of the blank com.cfg file
        a. In C:\Program Files\Microsoft Host Integration Server\System\config create a folder called Blank
        b. Copy and paste the file com.cfg to the folder Blank
    3. SNACFG.exe #”C:\Program Files\Microsoft Host Integration Server\System\config \com.cfg”  @ C:\Files\HIS_Migrate\System\Config\HISconfig.txt /NOVALIDATEPRINTER  /V

- Edit the C:\Files\HIS_Migrate\savedConfig.config file to insert the correct password(s) for the account(s) the services will run as. For security purposes the password(s) are replaced with "PasswordReplacedByThis", the correct password(s) must be entered or the services will not start.  Note there may be multiple instances of the password element.
- Apply the saved configuration by opening an Administrative Windows Command Prompt and issuing the following command:

   C:\Files>**HisMigration.exe C:\Files\HIS_Migrate /Apply**

## Additional Considerations

- When migrating to a new system, you may need to manually update the IPDLC link Services configuration of the network adapter(s).
- If the configuration to be migrated contains SNA Print Sessions, ensure that the same printers are configured on the new system.

## See Also

[HIS Migration Tool](../install-and-config-guides/his-migration-tool.md)  
[Same Server Migration](../install-and-config-guides/same-server-migration.md)
