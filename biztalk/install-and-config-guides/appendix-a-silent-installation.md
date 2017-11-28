---
title: "Appendix A: Silent Installation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94ded6b3-13ca-47e6-a038-254514f500e7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix A: Silent Installation
This topic lists the steps to create a silent installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## Create a Silent Installation  
  
1.  Click **Start**, click **All Programs**, click **Accessories**, and then click **Command Prompt**.  
  
2.  Go to the installation location. In the command prompt, type `setup.exe /``<command name> <options>`, and then press **ENTER**. The log file shows the installation status.  
  
|Command name|Option|Description|  
|------------------|------------|-----------------|  
|/HELP, or /?, or /H||Provides help and quick reference.|  
|/QUIET||Suppresses UI during setup – all dialog boxes, errors, or prompts requiring user input. All messages are entered into the setup log file. **Note:**  The Quiet flag cannot be specified for an upgrade, because upgrade requires user confirmation of selected options.|  
|/CABPATH|\<*CAB file location*\>|Indicates the location of the redistributable CAB file.|  
|/S|\<*Configuration XML file*\>|Performs a silent installation of features found in the specified configuration file. **Note:**  To install all features, specify ALL for the `InstalledFeature` parameter of the configuration XML file.|  
|/PASSIVE||Performs a passive installation. The setup program only displays the progress bar.|  
|/NORESTART||Suppresses restart prompts and automatic restarts at the end of the installation.|  
|/FORCERESTART||Always forces a restart after the installation is complete.|  
|/PROMPTRESTART||Prompts the user before restarting.|  
|/X or /UNINSTALL||Uninstalls [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|/L|\<Logfile\> [i][w][e][a][r][u][c][m][p][v][*]|Writes logging information to a log file to the specified path. Always uses verbose Windows Installer logging and it appends to an existing file.<br /><br /> The following flags indicate which information to log:<br /><br /> i - Status messages<br /><br /> w - Nonfatal warnings<br /><br /> e - All error messages<br /><br /> a - Startup of actions<br /><br /> r - Action-specific records<br /><br /> u - User requests<br /><br /> c - Initial user interface parameters<br /><br /> m - Out-of-memory<br /><br /> p - Terminal properties<br /><br /> v – Verbose output<br /><br /> * - All|  
|/IGNOREDEPENDENCIES||Bypasses the checks for downloadable prerequisites.|  
|/INSTALLDIR \<*install path*\>|\<*program files folder\>*|Specifies the full path to product install location.|  
|/COMPANYNAME|\<*company name*\>|Sets the company or organization name.|  
|/USERNAME|\<*user name*\>|Sets the user name.|  
|/ADDLOCAL ALL||Installs all features. For more information about ADDLOCAL command, see [Listing of Values for the ADDLOCAL Command](http://go.microsoft.com/fwlink/p/?LinkID=189319).|  
|/REMOVE ALL||Removes all features.|  
|/REPAIR ALL||Repairs all features.|  
|/CEIP||Enables Customer Experience Improvement Program (CEIP)|  
|/PRODUCT UDDI||Installs UDDI|  
|msiexec.exe /i  [MSIPATH] INSTALLDIR=[INSTALLDIRPATH] DATADIR=[DATADIRPATH] SQLSERVERMACHINENAME=[SQLSERVERNAME] OVERWRITERFIDSTORE=1 INSTALLLEVEL=5 /lvxp RfidServicesInstall.txt /q<br /><br /> For example: msiexec.exe /i "\\\ABC\XYZ\RFID_x86\RfidServices.msi" INSTALLDIR=“C:\Program Files\Microsoft BizTalk RFID\” DATADIR=“C:\Program Files\Microsoft BizTalk RFID\” SQLSERVERMACHINENAME=(local) OVERWRITERFIDSTORE=1 INSTALLLEVEL=5 /lvxp RfidServicesInstall.txt /q||Installs Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] RFID|  
  
 **Additional**  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables automated electronic software distribution, also known as a Silent Installation. A silent installation does the following:  
  
    -   Installs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on computers that have the same configuration.  
  
    -   Lets system administrators install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on remote computers without user intervention.  
  
    -   A user does not have to monitor the installation and provide input.  
  
-   To create a silent installation, use the command-line options to suppress all interaction.  
  
-   When you complete a silent installation, no messages are displayed in the command window. Use the installation log file to review the status.  
  
