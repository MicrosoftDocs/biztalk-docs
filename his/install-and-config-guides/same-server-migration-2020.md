---
description: "Learn how to use the HIS Migration tool to migrate from an earlier edition of Host Integration Server to Host Integration Server 2020 or 2016 on the same server."
title: "Same Server Migration with the HIS Migration tool"
ms.custom: ""
ms.date: "04/16/2021"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Same Server Migration with the HIS Migration tool

The HIS Migration tool allows you to migrate from an earlier edition of Host Integration Server to Host Integration Server 2020 or 2016 on the same server. The migration tool gets the configuration information before uninstalling the older version of Host Integration Server. This configuration information can be applied to the new install of Host Integration Server.

## Steps for Same Server Migration

- These instructions assume the migration tool is downloaded to a local `c:\Files` directory.
- Confirm the existing platform meets the [HIS 2020 system requirements](../install-and-config-guides/system-requirements-2020.md). Notice that .NET Framework 4.8 is required.
- Open a command prompt as administrator, go to `c:\Files`, and run the following command:

  ```cmd
  HisMigration.exe c:\Files\HIS_Migrate /Save
  ```
    
  > [!NOTE]  
  > `c:\Files\HIS_Migrate` must exist, and have no files in it.

- Uninstall the older HIS version (**Control Panel** > **Programs**).
- Install Host Integration Server 2020 or 2016. Don't run the Configuration Wizard.
- Edit the `c:\Files\HIS_Migrate\savedConfig.config` file to insert the correct password(s) for the account that the services run as. For security purposes, the password(s) are replaced with `PasswordReplacedByThis`. The correct password(s) must be entered, or the services won't start. There may be multiple instances of the password element.
- To refresh the new environment variables from the Host Integration Server installation, and save the configuration:
  1. Open a new command prompt as administrator, and go to `c:\Files`.
  2. Run: `HisMigration.exe c:\Files\HIS_Migrate /Apply`.

## Additional Considerations

- When migrating a multi-server subdomain, start the migration with the secondary server. When all of these servers are migrated, then migrate the primary server. Be sure to migrate the primary server last.
- The migration of servers configured to use a remote SNA Gateway isn't currently supported.  Support is planned in the next cumulative update.
- After the migration, when you're ready to allow access to the services, manually enable the firewall rules.
- For HIP Services, the migration tool examines the `HIPService.exe.config` contents for the `assemblyPath` of the HIP Objects. If the `assemblyPath` points to an HIS product path, such as `%snaroot%\TIM`, then the HIP Objects are moved to the new HIS TIM folder. If the `assemblyPath` is to a custom directory, then that directory is created, and the objects are copied to it.
- The migration tool doesn't examine the server for Application Integration Windows Initiated Programs (WIP). If these programs exist on the server, then look at the app.config files for these programs. Confirm the app.config file contents use the up-to-date locations on the server.
- If upgrading from HIS 2013 to HIS 2020 or 2016, then both WIP and HIP programs, and TI Assemblies must be recompiled to work with these HIS versions.

  Be sure to:

  - Add new references to the HIS TI runtime assemblies.
  - Update the .config files to use version 10.0, instead of version 9.0.
  - Projects must use .Net 4.8 or 4.6.
  - In the HIS designer, open any TI .hidx file(s), and save them. This step generates updated dll(s). This step isn't required when migrating from HIS 2016 to HIS 2020.

- For both WIP and HIP, all configuration must be done in the .config files. No configuration information is read from the registry.
- The Visual Studio Integration feature is no longer migrated by this tool. In HIS 2020, the Visual Studio extenstions are re-written as a VSIX package. It isn't possible to support the migration from the old VSIP packages. To restore this feature, run the configuration wizard, and enable the Visual Studio Integration feature.

## Next steps

[HIS Migration Tool](his-migration-tool-2020.md)  
[Server to Server Migration](server-to-server-migration-2020.md)
