---
title: "Install the FileAct and InterAct Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf387d59-373b-4151-9dfd-30c511978862
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install the FileAct and InterAct Adapter
This section provides instructions to install [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] – for SWIFT. Before you install the adapters, you must install the prerequisite software.  
  
## Prerequisites  

* Sign in with an account that is member of the local administrators group, and a member of the BizTalk Server Administrators group
  
## Step 1: Install BizTalk Server and configure BAM

1. Install [BizTalk Server 2016](../../install-and-config-guides/biztalk-server-2016-what-s-new-and-installation.md), or [BizTalk Server 2013 R2 / 2013](../../install-and-config-guides/biztalk-server-2013-and-2013-r2-what-s-new-install-and-upgrade.md), and install Business Activity Monitoring (BAM).

2. Configure [BizTalk Server](../../install-and-config-guides/configure-biztalk-server.md), and configure Business Activity Monitoring (BAM).
  
3. Make sure you have enough security privileges to access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. [Minimum Security Rights for BizTalk Server](http://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) is a great resource.
  
## Step 2: Install BizTalk Accelerator for SWIFT (A4SWIFT)  

Install and configure the [BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md).

  
## Step 3: Install SWIFTAlliance Gateway (SAG)  
 Before you install the FileAct and InterAct adapters, create the SAG Message Partners, End Points, and Routing Rules, and test the SAG connectivity on the computer where you install the FileAct and InterAct adapters.

See [https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway](https://www.swift.com/our-solutions/interfaces-and-integration/alliance-gateway) for specific details on the SWIFTAlliance Gateway.  

## Step 4: Install the BizTalk FileAct and InterAct adapters  
  
1. Run the **Setup.exe** as administrator to start the installation.  
  
2. Select **Install**.  
  
3. Enter your user name and organization name, and then select **Next**.  
  
4. **Accept** the license agreement.
  
5. On the **Installation Options** page, do one of the following:  
  
   - Select the **Complete** option to install all components of the FileAct and InterAct adapters.  
  
   - Select the **Custom** option to choose which components to install.  
  
     Verify the installation location, or select **Browse** to select a different installation location. Select **Next**.  
  
6. On the **Summary** page, select **Install** to install the listed components.  
  
   > [!NOTE]
   >  When **Run Configuration Wizard** is selected (the default), the **Microsoft BizTalk FileAct and InterAct Adapter Configuration** wizard runs automatically when you select **Finish**.  
  
7. When the installation completes, select **Finish**. 

## Next steps

[Configure the FileAct and InterAct adapter](../../adapters-and-accelerators/fileact-interact/configure-the-fileact-and-interact-adapter.md)  
[Sample InterAct and FileAct messages](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md)  
[Uninstall or repair the FileAct and InterAct adapter](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[Read the installation known issues](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
  
## See Also  
[Getting started with the FileAct and InterAct adapters](../../adapters-and-accelerators/fileact-interact/getting-started-with-the-fileact-and-interact-adapters.md)  
[Understanding FileAct and InterAct adapter architecture](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)