---
description: "Learn more about: Install and configure HIS 2020"
title: "Install HIS 2020 | Microsoft Docs"
ms.custom: ""
ms.date: "5/4/2020"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80c18554-aa15-463e-a139-13f25db7d571
caps.latest.revision: 8
author: "christopherhouser"
ms.author: "hisdocs"
manager: "mijacobs"
---

# Install and configure HIS 2020

This installation guide includes basic steps to use the Host Integration Server 2020 setup installation and configuration.

## Before you begin

- Read the [Release Notes](../install-and-config-guides/release-notes-2020.md).
- Confirm the [System Requirements](../install-and-config-guides/system-requirements-2020.md) are installed.

## Installation

1. Double-click the **HIS2020_Server_EN.msi** file.

2. In the **License Agreement**, accept the **End User License Agreement**. To customize your installation (optional):

    1. Select **Advanced**.

    2. In **Destination Folder**, you can optionally change the installation drive and directory.

    3. In **Product Features**, you can optionally choose the feature areas, tools, and sub features.

        Select **Install** to continue.

3. When complete, select **Finish**.

## Configuration

After you successfully install HIS, run configuration to:

- Define security groups.
- Enter service credentials.
- Enable (configures) or disable (un-configures) features and tools. For example, configuration registers BizTalk Adapters and Visual Studio design tools.

## Uninstall

1. Open **Programs and Features**.

2. In the list, select **Microsoft Host Integration Server 2020** > **Uninstall**.

3. When prompted if you're sure, select **Yes**.

## In-place upgrade of HIS 2016

1. Double-click the **HIS2020_Server_EN.msi** file.

2. In the **License Agreement**, accept the **End User License Agreement**.

3. Select **Install** to continue with the upgrade.

4. When complete, select **Finish**.

After an in-place upgrade from HIS 2016 to HIS 2020, if the configuration tool isn't allowed to open at the end of setup, then the services may fail to start. Many of the services require the correct versions of the Visual C++ Runtime DLLs. These DLLs are installed by the configuration tool when it first starts. To fix this issue, open the Start menu, and open the configuration tool.

## Unattended Installation

**Install using the following command**:

```Output
msiexec /i HIS2020_Server_EN.msi /quiet
```

A setup log is written to the `%temp% folder`.

To confirm the installation, go to `\Program Files\Microsoft Host Integration Server`, and confirm the HIS files are there.

**Uninstall using the following command**:

```Output
msiexec /x HIS2020_Server_EN.msi /quiet
```

A setup log is written to the `%temp% folder`.

To confirm the uninstallation, go to `\Program Files\Microsoft Host Integration Server`, and confirm the HIS files are removed.

For a list of MSIEXEC command line options, see the [Installer documentation](/windows/win32/msi/command-line-options) (https://go.microsoft.com/fwlink/p/?LinkId=799793).

## Unattended Configuration

**Configure using the command:**

```Output
ConfigurationWizard.exe /APPLY HIS2020.configurationfile.config
```

The config file can be created by running the Configuration Wizard as a UI program. Run ConfigurationWizard.exe with no parameters, or run Configuration under the Microsoft Host Integration Server 2020 programs list.

**Unconfigure using the command:**

```Output
ConfigurationWizard.exe /u
```

## Unattended Installation and Configuration

**Install and Configure using the command:**

```Output
msiexec /i HIS2020_Server_EN.msi /quiet CONFIGURATIONFILE= HIS2020.configurationfile.config
```

## Disable Telemetry

**Opt-out through UI**

In the Configuration tool > Common setting panel, uncheck **Turn on Telemetry to help improve the quality, reliability and performance**.

**Opt-out through PowerShell**

You can use the following PowerShell script to enable or disable telemetry:

`Import-Module Microsoft.HostIntegration.PowerShell`

```Output
$c = Import-HisConfiguration
$cs = $c | Get-HisFeature -CommonSettings
$cs.EnableTelemetry = $false
$c.Apply()
```

## Next steps

[Get started using Host Integration Server](../core/host-integration-server-core-documentation.md).