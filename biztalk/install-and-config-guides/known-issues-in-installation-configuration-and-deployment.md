---
title: Known issues in installation, configuration, and deployment
description: Learn about known issues around installation, configuration, and deployment for BizTalk Server.
ms.prod: biztalk-server
ms.topic: conceptual
ms.date: 06/08/2017
---

# Known issues around installation, configuration, and deployment for BizTalk Server

## Some BizTalk EDI/AS2 artifacts are still active after unconfiguring

After you unconfigure the BizTalk EDI/AS2 feature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some BizTalk Server artifacts related to EDI and AS2 processing will still be active in the context of the BizTalk group configuration. These artifacts will include EDI and AS2 pipelines and the batching orchestration. As a result, you will still be able to perform basic EDI and AS2 processing even after unconfiguring the BizTalk EDI/AS2 feature.

### Cause

There are active ports associated with EDI and AS2 processing. Some artifacts will continue to function while these ports remain active.

### Resolution

To disable all EDI/AS2 artifacts, you should disable, stop, or delete the ports associated with EDI and AS2 processing.

## If the BizTalk Server computer or SQL Server computer is renamed after BizTalk Server configuration, the configuration wizard will fail

This problem may manifest itself in several ways:

- The BizTalk Server Configuration will load the Overview page correctly, but when attempting to configure a feature the feature options do not display on the screen.

- The configuration wizard cannot connect to the SQL Server.

- Attempting to Unconfigure All unconfigures some features, but not all.

### Cause

The BizTalk Server configuration stores the computer network name. When the computer is renamed the BizTalk Server Configuration and configuration wizard cannot locate the BizTalk Server. A similar problem will occur if the SQL Server computer is renamed after BizTalk Server is configured.

### Resolution

Do not rename the BizTalk Server computer or the SQL Server computer. If a server must be renamed, unconfigure all BizTalk Features before renaming the computer. After renaming the computer, reconfigure BizTalk Server features.

## The BizTalk Server Business Rules Configuration Wizard fails

- The Business Rules Configuration Wizard fails with the error “Configuration failed for some components and no settings were applied for those components”.

- On BizTalk Server computers for which the Business Rules Engine has already been successfully configured, the Rules Engine Update service fails to start and cannot be started manually.

  When this problem occurs, an error similar to the following may be generated in the BizTalk Server computer Application log:

  ```
  Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132
  ```

### Cause

The Microsoft Malware Protection Center released an updated signature file to address a possible threat from SettingsModifier:Win32/PossibleHostsFileHijack. This updated signature file can cause Microsoft Malware Detection software such as Windows Defender to update the local HOSTS file to mitigate threats from SettingsModifier:Win32/PossibleHostsFileHijack. As a result of these changes, the BizTalk Server Rules Engine Update service may fail to start.

### Resolution

Update the local HOSTS file to include the following line:

```
127.0.0.1         localhost
```

The HOSTS file is located in the %systemroot%\drivers\etc\ directory.

> [!NOTE]
> For more information about the possible threat from the malware named **SettingsModifier:Win32/PossibleHostsFileHijack**, see 
> [Microsoft Security Intelligence page about this threat](https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?name=settingsmodifier%3Awin32%2Fpossiblehostsfilehijack) and [Microsoft Support page about "Hosts file is detected as malware in Windows Defender"](https://support.microsoft.com/topic/hosts-file-is-detected-as-malware-in-windows-defender-4320fa8b-0d54-1129-db85-61f095144521).

## Enlistment of an orchestration fails if referenced assemblies are missing from the GAC/Mgmt DB

Enlistment of an orchestration fails if references (C# assemblies which are referenced to orchestrations) are missing from the GAC/Mgmt db. During re-deployment, there may be a need to enlist the orchestration based on its existing state. If references are missing then the deployment also fails.

### Cause

Referenced assemblies are missing from GAC/Mgmt db.

### Resolution

Add the referenced assemblies in GAC or add them as resources, so that they are stored in Mgmt db and are accessible during enlistment of orchestration.

## Community blog: BizTalk 2013 R2 bugs, issues & quirks

[BizTalk Server 2013 R2 known bugs, issues, quirks](https://cdijkgraaf.wordpress.com/2016/08/12/biztalk-2013-r2-known-bugs-issues-quirks/)

## See also

[Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)

[Configuring BizTalk Server on an Azure VM](/previous-versions/azure/jj248689(v=azure.100))

[Configure BizTalk Server in a Cluster](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)

[Securing Your BizTalk Server Deployment](../install-and-config-guides/securing-your-biztalk-server-deployment.md)