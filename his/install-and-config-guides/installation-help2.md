---
title: "Installation help | Microsoft Docs"
ms.custom: ""
ms.date: 10/24/2016
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4933ab5c-56c4-468c-a203-352eedd90ac6
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
robots: noindex,nofollow
---
# Installation guidance
Use this topic to navigate through the Installation user interface.  
  
## Autorun  
 **Planning**  
  
 We recommend that you read the Host Integration Server [Installation Guide](../install-and-config-guides/installation-guide1.md), which covers the following topics:  
  
- System requirements  
  
- Feature installation and configuration prerequisites  
  
- Supported host systems  
  
- Product installation and configuration (upgrades and setup options)  
  
- Installing and configuring HIS and Enterprise Single Sign-on (ESSO)  
  
- Uninstalling HIS and ESSO  
  
  **Installation**  
  
  Click **Host Integration Server** to close launch the Installation Wizard.  
  
  **Exit**  
  
  Click **Exit** to close the Autorun program.  
  
## Welcome  
 The Installation Wizard for Host Integration Server is similar to other Windows-based applications. The Installation Wizard calls Windows Installer and coordinates the installation process from beginning to end, terminating when the last component is installed. If you do not have the software prerequisites installed, then the Installation Wizard will install them from the Web or a pre-downloaded CAB file.  
  
## License Agreement  
 The License agreement dialog box allows you to read and review the license use terms for Host Integration Server. Please read the license use terms.  
  
1.  Click **Yes** to accept the license use terms and continue with the installation process. Click **No** to reject the license use terms and close the installation wizard.  
  
2.  Click **Cancel** to close the Installation Wizard.  
  
3.  Click **Next** to continue with the installation process.  
  
## Component Installation  
 The Installation Wizard displays components that are available with this version of Host Integration Server.  
  
 **Available Components**  
  
1. Select to install either **Server** or **Client** components. By default, the Installation Wizard pre-selects Server components.  
  
    When installing Server, you may choose whether to install Enterprise Single Sign-On. The Installation Wizard installs all other server components.  
  
    When installing Client, you may not choose whether to install individual components. The Installation Wizard installs all client components.  
  
2. Optionally, click the plus sign (+) to expand the list of available components. If a software perquisite is not present on the computer, then the Installation Wizard will disable a component and display a disabled empty checkbox.  
  
   **Description**  
  
   In the **Description** field, the Installation Wizard displays additional information on the available components.  
  
   **Space allocation**  
  
   The Installation Wizard displays the space required to install the product. Optionally, click **Space Allocated Details** to view available space on the selected storage drive.  
  
   **Install to**  
  
3. Choose an installation path. By default, the Installation Wizard will install the product into the folder `C:\Program Files\Microsoft Host Integration Server 20xx\`. Click **Browse** to select a different installation folder.  
  
4. Click **Back** to return to the previous dialog.  
  
5. Click **Cancel** to close the Installation Wizard.  
  
6. Click **Next** to continue with the installation process.  
  
## Installation Summary  
 **Summary**  
  
 This is the Installation Summary screen. Please review the perquisites and components that will be installed. Click Back to make changes on the previous screen. Click Install to continue with Setup.  
  
 **Set**  
  
1.  Optionally, click **Set** to select automatic logon and enter your credentials. If the Setup Wizard needs to reboot the computer during setup, then the Setup Wizard will use these credentials to automatically log into the computer and continue the installation process.  
  
2.  Click **Back** to return to the previous dialog  
  
3.  Click **Cancel** to close the Installation Wizard.  
  
4.  Click **Next** to continue with the installation process.  
  
## Installation Completed  
 **Logfile**  
  
 Click **Logfile** to review the setup log. The Host Integration Server setup log contains information, warning and errors from the installation process. You can use this log file for troubleshooting and when running setup in unattended mode.  
  
 **Check for Updates**  
  
 Click the **Check for Updates** button to launch the Windows Update, and then install available updates to Host Integration Server.  
  
 **Launch Host Integration Server Configuration**  
  
 Click **Finish** to close the Host Integration Server Setup Wizard and launch the Host Integration Server Configuration wizard.  
  
## Microsoft Update  
 **Check for Updates**  
  
 Click the **Check for Updates** button to launch the Windows Update, and then install available updates to Host Integration Server.  
  
 **Launch Host Integration Server Configuration**  
  
 Click **Finish** to close the Host Integration Server Setup Wizard and launch the Host Integration Server Configuration wizard.  
  
## Program Maintenance  
 **Modify**  
  
 This option displays the Component Selection dialog box that you can use to select the features that you want to install.  
  
 **Repair**  
  
 Repair installation errors in the program. This option fixes missing or corrupt files, shortcuts, and registry entries.  
  
 **Remove**  
  
 Remove Host Integration Server from your computer.  
  
## Uninstall Complete  
 **Logfile**  
  
 Click **Logfile** to review the setup log. The Host Integration Server setup log contains information, warning and errors from the uninstall process. You can use this log file for accounting troubleshooting.  
  
 **Finish**  
  
 Click **Finish** to close the Host Integration Server Installation Wizard.  
  
## Installation Cancelled  
 The Installation Wizard is canceling the installation process.  
  
## Upgrade Summary  
 The Installation Wizard displays summary information on the upgrade process.  
  
## See Also  
 [Installing HIS 2013](../install-and-config-guides/installing-his-2013.md)