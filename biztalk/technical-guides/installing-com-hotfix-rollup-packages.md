---
description: "Learn more about: Installing COM+ Hotfix Rollup Packages"
title: "Installing COM+ Hotfix Rollup Packages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing COM+ Hotfix Rollup Packages
> [!NOTE]
>  This topic is applicable only for Windows Server 2003.

 You should install the last version of the Windows Server 2003 COM+ hotfix rollup package and latest version of the Distributed Transaction Coordinator (DTC) rollup package. This is because the packages include many performance and stability fixes.

 You should install these rollups on all computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and on all computers running SQL Server. The rollups are especially important for your BizTalk solution to perform well in high-throughput scenarios.

 The DTC issues that have been fixed are as follows:

- Unexpected DTC shutdown

- Memory fragmentation issues

- DTC may stop responding under load

- DTC may leak memory or stop responding when used with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]

- Performance of DTC under load has been improved

## Installing the COM+ Rollup Package
 COM+ is no longer releasing rollup packages. Follow this information to install the last COM+ package:

-   The final version of the COM+ rollup is the “Windows Server 2003 Post-Service Pack 2 COM+ 1.5 Hotfix Rollup Package 12”. This hotfix will install on any version of Windows Server 2003, even those without a service pack installed. 

## Installing the DTC Rollup Package
 DTC will be releasing rollup packages independent of COM+. Follow this information to install the latest DTC package:

-   The information about the latest DTC hotfix rollup package can be found by searching [https://support.microsoft.com](https://support.microsoft.com/) for the phrase (including the quotes):

    ```
    "MS DTC Hotfix Rollup Package"
    ```
