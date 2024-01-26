---
description: "Learn how to use the HIS Migration tool to migrate from an earlier edition of Host Integration Server to Host Integration Server 2016 on the same server."
title: "Same Server Migration"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Same Server Migration

## Overview

The HIS Migration tool allows you to migrate from an earlier edition of Host Integration Server to Host Integration Server 2016 on the same server. The migration tool harvests the configuration information prior to uninstalling the older version of Host Integration Server. That configuration information can be applied to the new install of Host Integration Server 2016.

## Steps for Same Server Migration
- These instructions assume the migration tool is downloaded to a local C:\Files directory.
- Verify the existing platform meets HIS 2016 requirements (see [System Requirements](../install-and-config-guides/system-requirements.md)). Note that .NET Framework 4.6 must be installed.
- Open an Administrative Windows Command Prompt and issue the following command:

    C:\Files>**HisMigration.exe C:\Files\HIS_Migrate /Save**   
    
    > [!NOTE]  
    > C:\Files\HIS_Migrate must exist and have no files in it  

- Uninstall the older version of HIS using Control Panel - Programs and Features
- Install Host Integration Server 2016, but do not run the Configuration Wizard.
- Edit the C:\Files\HIS_Migrate\savedConfig.config file to insert the correct password(s) for the account that the services will run as. For security purposes the password(s) are replaced with "PasswordReplacedByThis", the correct password(s) must be entered or the services will not start.  Note there may be multiple instances of the password element.
- Open a new Administrative Windows Command Prompt to refresh the new environment variables from the Host Integration Server 2016 installation.
- Apply the saved configuration by opening an Administrative Windows Command Prompt and issuing the following command: 

   C:\Files>**HisMigration.exe C:\Files\HIS_Migrate /Apply**

## Additional Considerations
- When migrating a multi-server subdomain the primary server needs to be the last server migrated.  Start the migration with the secondary server first, once all of these servers have been migrated, the primary can be migrated.  
- The migration of servers configured to use a remote SNA Gateway is not currently supported.  Support for this scenario is planned for the next cumulative update.   
- After the migration, you will need to manually enable the firewall rules when you are ready to allow access to the services.  
- For HIP Services, the migration tool examines the contents of the HIPService.exe.config for the assemblyPath of the HIP Objects – if the assemblyPath points to an HIS Product path (for example: %snaroot%\TIM), the HIP Objects are moved to the HIS 2016 TIM folder, if the assemblyPath is to a custom directory, that directory is created and the objects are copied there.
- The migration tool does not examine the server for Application Integration Windows Initiated Programs (WIP). If these exist on the server it is important to examine the app.config files for those programs to verify the contents point to up to date locations on the server.
- For both WIP and HIP, the programs and TI Assemblies will need to be recompiled to work with HIS 2016. New references to the HIS 2016 TI runtime assemblies and updates to the .config files to point to version 10.0 instead of 9.0 must be made and the projects must use .Net 4.6. In addition, any TI .hidx file(s) must be opened and saved again in HIS 2016 designer to generate updated dll(s).
- For both WIP and HIP, all configuration must be done in the .config files – there is no configuration information that will be read from the registry.

## See Also
[HIS Migration Tool](../install-and-config-guides/his-migration-tool.md)  
[Server to Server Migration](../install-and-config-guides/server-to-server-migration.md)
