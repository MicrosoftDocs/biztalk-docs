---
title: "Host Integration Server server-to-server Migration | Microsoft Docs"
ms.custom: ""
ms.date: "5/13/2020"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc4b1593-9301-423e-b515-a6a59230e78f
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs"
manager: "dougeby"
---

# Server to Server migration

## Overview

The HIS Migration tool can be used to:

- Move older HIS version configurations to a Host Integration Server 2020 or 2016 server.
- Move the Host Integration Server 2020 or 2016 configuration from one server to another srver.

## Steps to migrate HIS to HIS on a different server

- These steps assume the migration tool is downloaded to a local `c:\Files` directory.
- On the first Host Integration Server, open a command prompt as administrator, go to `c:\Files`, and run the following command:

  ```cmd
  HisMigration.exe C:\Files\HIS_Migrate /Save
  ```

  > [!NOTE]
  > `c:\Files\HIS_Migrate` must exist, and have no files in it.

- From the first HIS server, copy the `c:\Files` directory and subdirectory, and paste it to the new HIS server.
- Use the `snacfg.exe` tool to update the `c:\Files\HIS_Migrate\System\Config\com.cfg`:

  1. Generate a blank command file using the `/print` option:
  
      ```cmd
      SNACFG.exe #c:\Files\HIS_Migrate\System\Config\com.cfg /print > HISconfig.txt
      ```

  2. In the command file, change the server name from the existing server name to the new server name.
  
  3. Install Host Integration Server 2020 or 2016. Don't run the Configuration Wizard. 
  
  4. Make a copy of the blank `com.cfg` file:

      1. In `c:\Program Files\Microsoft Host Integration Server\System\config`, create a folder named `Blank`.
      2. Copy the file com.cfg from C:\Program Files\Microsoft Host Integration Server\System\config to the folder Blank.
      
      [!NOTE]
      This will allow you to repeat this step with a clean com.cfg file

  5. To generate a new com.cfg file, use the snacfg.exe tool with the new command file:

      ```cmd
      SNACFG.exe #”C:\Program Files\Microsoft Host Integration Server\System\config\com.cfg”  @ C:\Files\HIS_Migrate\System\Config\HISconfig.txt /NOVALIDATEPRINTER  /V
      ```

- Edit the `c:\Files\HIS_Migrate\savedConfig.config` file to insert the correct password(s) for the account(s) that the services run as. For security purposes, the password(s) are replaced with `PasswordReplacedByThis`. The correct password(s) must be entered, or the services won't start. There may be multiple instances of the password element.
- To apply the saved configuration:
  1. Open a command prompt as administrator, and go to `c:\Files`.
  2. Run: `HisMigration.exe c:\Files\HIS_Migrate /Apply`.

## Additional Considerations

- When migrating to a new system, you may need to manually update the IPDLC link Services configuration of the network adapter(s).
- If the configuration to be migrated includes SNA Print Sessions, then confirm the same printers are configured on the new system.

## Next steps

[HIS Migration Tool](../install-and-config-guides/his-migration-tool-2020.md)  
[Same Server Migration](../install-and-config-guides/same-server-migration-2020.md)
