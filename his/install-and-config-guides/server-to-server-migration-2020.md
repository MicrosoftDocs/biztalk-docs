---
title: Host Integration Server server-to-server Migration
description: Learn more about server to server migration for Host Integration Server.
ms.service: host-integration-server
ms.topic: article
ms.date: 01/25/2023
---

# Server to Server migration

## Overview

The HIS Migration tool can be used to:

- Move older HIS version configurations to a Host Integration Server 2020.
- Move the Host Integration Server 2020 configuration from one server to another server.

## Steps to migrate HIS to HIS on a different server

- These steps assume the migration tool is downloaded to a local **C:\Files** directory.
- On the first Host Integration Server, open a command prompt as administrator, go to **C:\Files**, and run the following command:

  ```cmd
  HisMigration.exe C:\Files\HIS_Migrate /Save
  Saving Configuration
  Saving Files
  If the Configuration is to be moved to a new machine, please note:
  
  savedConfig.config: You must edit this file to change the Passwords of all Services before restoring the configuration. If this machine is a primary sub-domain controller, and you want another sub-domain on the new machine, please edit this file.
  
  COM.CFG : COM.CFG may need changing to have a new Server name.
  
  comtblg.dat : If the COMTBLG File is not referenced via the SNARoot environment variable, the saved configuration file may need editing.
  ```

  > [!NOTE]
  > `C:\Files\HIS_Migrate` must exist, and have no files in it.

- From the first HIS server, copy the `C:\Files` directory and subdirectory, and paste it to the new HIS server.
- Use the `SNACFG.exe` tool to update the `C:\Files\HIS_Migrate\System\Config\com.cfg`:

  1. Generate a blank command file using the `/PRINT` option:
  
      ```cmd
      SNACFG.exe #C:\Files\HIS_Migrate\System\Config\com.cfg /print > HISconfig.txt
      Config file is: C:\Files\HIS_Migrate\System\Config\com.cfg
      ```

  2. The HISconfig.txt file will be generared in the Files directory. If the new server has a different name, edit HISconfig.txt and replace all instances of the old name with the new name.
  
  3. Install Host Integration Server 2020. Don't run the Configuration Wizard.
  
  4. Make a copy of the blank `COM.cfg` file:

      1. In `C:\Program Files\Microsoft Host Integration Server\System\config`, create a folder named `Blank`.
      2. Copy the file com.cfg from C:\Program Files\Microsoft Host Integration Server\System\config to the folder Blank.
      
      [!NOTE]
      This will allow you to repeat this step with a clean com.cfg file

  5. To generate a new com.cfg file, use the snacfg.exe tool with the new command file:

      ```cmd
      SNACFG.exe #”C:\Program Files\Microsoft Host Integration Server\System\config\com.cfg”  @C:\Files\HISconfig.txt /NOVALIDATEPRINTER  /V
      ```

- Edit the `C:\Files\HIS_Migrate\savedConfig.config` file to insert the correct password(s) for the account(s) that the services run as. For security purposes, the password(s) are replaced with `PasswordReplacedByThis`. The correct password(s) must be entered, or the services won't start. There may be multiple instances of the password element.
- To apply the saved configuration:
  1. Open a command prompt as Administrator, and go to `C:\Files`.
  2. Run: `HisMigration.exe C:\Files\HIS_Migrate /Apply`.

## Additional Considerations

- When migrating to a new server, you may need to manually update the IPDLC link Services configuration of the network adapter(s).
- If the configuration to be migrated includes SNA Print Sessions, then confirm the same printers are configured on the new server.

## Next steps

[HIS Migration Tool](../install-and-config-guides/his-migration-tool-2020.md)  
[Same Server Migration](../install-and-config-guides/same-server-migration-2020.md)