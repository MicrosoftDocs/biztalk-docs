---
description: "Learn more about: Install and configure HIS 2016"
title: "Install HIS 2016"
ms.custom: ""
ms.date: 6/13/2018
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Install and configure HIS 2016
This installation guide provides basic instructions for using the [!INCLUDE[his2016](../includes/his2016-md.md)] setup installation and configuration.

## Before you begin

-   Read the [Release Notes](../install-and-config-guides/release-notes.md)

-   Refer to the [System Requirements](../install-and-config-guides/system-requirements.md)

## Installation

1. Double-click the **HIS2016_Server_EN.msi** file.

2. In the **License Agreement**, accept the **End User License Agreement**. To customize your installation (optional):

   1. Select **Advanced**.

   2. In **Destination Folder**, you can optionally change the installation drive and directory.

   3. In **Product Features**, you can optionally choose the feature areas, tools, and sub features.

      Select **Install** to continue.

3. When complete, select **Finish**.

## Configuration
 After you successfully install HIS, run configuration to:

-   Define security groups

-   Enter service credentials

-   Enable (configures) or disable (un-configures) features and tools. For example, configuration registers BizTalk Adapters and Visual Studio design tools.

## Uninstall

1. Open **Programs and Features**.

2. In the list, select **Microsoft [!INCLUDE[his2016](../includes/his2016-md.md)]**, and then select **Uninstall**.

3. When prompted if you're sure, select **Yes**.

## Unattended Installation
 **Install using the following command**:

```Output
msiexec /i HIS2016_Server_EN.msi /quiet
```
*Note: A setup log will be written to the %temp% folder*

 Verify the installation by going to ***drive*:\Program Files\Microsoft Host Integration Server 2016**, and confirming the HIS files are there.

 **Uninstall using the following command**:

```Output
msiexec /x HIS2016_Server_EN.msi /quiet
```
*Note: A setup log will be written to the %temp% folder*

 Verify the uninstallation by going to ***drive*:\Program Files\Microsoft Host Integration Server 2016**, and confirming the files are removed.

 For a list of MSIEXEC command line options, read the [Installer documentation](/windows/win32/msi/command-line-options) (https://go.microsoft.com/fwlink/p/?LinkId=799793).

## Unattended Configuration
**Configure using the command:**

```Output
ConfigurationWizard.exe /APPLY HIS2016.configurationfile.config
```
The config file can be created by running the Configuration Wizard as a UI program – either by running ConfigurationWizard.exe with no parameters or running Configuration under the Microsoft Host Integration Server 2016 programs list.

**Unconfigure using the command:**

```Output
ConfigurationWizard.exe /u
```


## Unattended Installation and Configuration
**Install and Configure using the command:**

```Output
msiexec /i HIS2016_Server_EN.msi /quiet CONFIGURATIONFILE= HIS2016.configurationfile.config
```

## Disable Telemetry
**Opt-out through UI**

On the Common setting panel of the Configuration tool, uncheck **Turn on Telemetry to help improve the quality, reliability and performance**.

**Opt-out through PowerShell**

You can use the following PowerShell script to enable or disable telemetry:

Import-Module Microsoft.HostIntegration.PowerShell
```Output
$c = Import-HisConfiguration
$cs = $c | Get-HisFeature -CommonSettings
$cs.EnableTelemetry = $false
$c.Apply()
```