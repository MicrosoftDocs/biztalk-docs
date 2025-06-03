---
description: "Learn more about: Step 1: Installing the Base Platform"
title: "Step 1: Installing the Base Platform"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Step 1: Installing the Base Platform
For the base platform, install Microsoft [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] and [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] Service Pack 2 on each server using the default installation options. Follow these recommendations:

## Pre-Installation

- Disable all antivirus software during software installation. Some antivirus software programs might prevent required software components from installing properly.

- Make sure that you enter the appropriate licensing information (maximum number of connections you have purchased per server). System performance can be affected by the number of available connections.

- Make sure that you have installed all the software prerequisites required for a BizTalk Server installation. For more information, see the [BizTalk Server What's New, Install, Configuration, and Upgrade](/biztalk/install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade) and [Install BizTalk Accelerator for SWIFT](/biztalk/adapters-and-accelerators/accelerator-swift/install-biztalk-accelerator-for-swift).

- Test all critical updates in an offline environment before installing them on your production servers.

- Make sure that you install all the applicable hotfixes for all the products that you install as part of your deployment. For more information, see the following sources:

  - Microsoft BizTalk Server Online Help

  - [BizTalk Server What's New, Install, Configuration, and Upgrade](/biztalk/install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade)

  - Microsoft website [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]

  - [Microsoft Download Center](https://www.microsoft.com/download)

  - [!INCLUDE[btsWinUpdate](../../includes/btswinupdate-md.md)] [Web site](https://go.microsoft.com/fwlink/?linkid=48687).

- To avoid virus attacks, install the platform from a CD and disconnect each server from the Internet by unplugging any cables and disabling any network adapters.

- Format a clean partition using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] NTFS file system.

## Active Directory

-   Create a domain user called **Admin** and add it to the local **Administrators** group on every computer in your deployment. At installation time, log on to the deployment servers using this domain account.

-   Do not configure any network adapters or join any domains at this time. This guide describes how to configure these settings later when you begin the deployment process.

## Internal Web Servers (MRSR site)

-   Make sure that Internet Information Services (IIS) is installed only on the MRSR site Servers.

-   Make sure that Internet Information Services (IIS) is not installed on the Internet Security and Acceleration (ISA) Server.

-   Make sure that the Message Queuing (MSMQ) service is installed only on the MRSR site Servers. If the BizTalk Messaging servers will also be used as the MRSR site Servers, do not install MSMQ on those servers.
