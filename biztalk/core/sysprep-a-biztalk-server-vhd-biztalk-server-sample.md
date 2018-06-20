---
title: "Sysprep a BizTalk Server VHD (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35f0146d-60ed-4265-983a-0e3665ef2ae4
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sysprep a BizTalk Server VHD (BizTalk Server Sample)
Sysprep creates a snapshot of a virtual machine with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed for quick deployment on other virtual machines.  
  
## Prerequisites  
 Before using Sysprep, you should have some knowledge of using virtual machines with Hyper-V. You should also have a virtual machine with a clean, typical installation of BizTalk Server and all of its prerequisites.  
  
 Sysprep will run on Windows Server 2008 and Windows Vista with SP1.  
  
## What This Sample Does  
 Sysprep creates a VHD of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation (including the operating system and all prerequisites) for quick deployment on other virtual machines. An image created using Sysprep will choose a new computer name in order to join the domain the first time it starts. To get BizTalk Server running properly, it is necessary to update various instances of the computer name that are stored in the registry and databases.  
  
 This document assumes that BizTalk Server is configured to run on a single computer, and shows how to update other instances of the computer name with the new name.  
  
## Where to Find This Sample  
 The sample is located in the following SDK location:  
  
 \<*Samples Path*\>\Admin\Sysprep\  
  
 The following table shows the files in this sample and describes their purpose.  
  
> [!NOTE]
>  The .vbs and .cmd files in the table below are all automated in the Sysprep answer files (Sysprep.xml and SetupCompletecmd.txt), and are listed here for reference only. If you do need to run these scripts manually, run them in the order that they appear in the table.  
  
|File|Description|  
|----------|-----------------|  
|Sysprep.xml|Answer file|  
|SetupCompletecmd.txt|Answer file|  
|ReplaceMachineName.vbs|Purpose: Opens a file and replaces all instances of a given string with the current computer name. Useful to prepare the other script and xml files, and to update bm.exe.config.<br /><br /> Usage: ReplaceMachineName.vbs \<file to open\> \<string to replace\>|  
|UpdateRegistry.vbs|Purpose: Updates the computer name stored in the BizTalk registry settings.<br /><br /> Usage: UpdateRegistry.vbs \<UpdateInfo.xml\>. Make sure to replace all instances of $(OLDCOMPUTERNAME) and $(NEWCOMPUTERNAME) in this xml file.|  
|UpdateDatabase.vbs|Purpose: Updates the computer name stored in the BizTalk Management databases.<br /><br /> Usage: UpdateDatabase.vbs \<UpdateInfo.xml\>|  
|UpdateBAMDb.vbs|Purpose: Updates the computer name stored in the BAM databases.<br /><br /> Usage: UpdateBamDb.vbs \<UpdateInfo.xml\>|  
|UpdateSSO.cmd|Purpose: Reconfigures the Enterprise Single Sign-on (SSO) secret server.<br /><br /> Usage: sso.cmd \<UpdateInfo.xml\>|  
|UpdateSqlServerAndInstanceName.cmd|Purpose: Reconfigures SQL and SQL Express, restarts a series of dependent services, and reregisters BAMAlerts.<br /><br /> Usage: Edit the script and replace all instances of $(NEWCOMPUTERNAME), and update the serviceusername and servicepassword for BAM Alerts. Then run UpdateSqlServerAndInstanceName.cmd passing the old computer name as the first argument.|  
  
## Creating the Answer Files and Running Sysprep  
  
#### To create the answer files  
  
1. Install and configure BizTalk Server on a virtual machine. Be sure to use default installation and configuration options, since Sysprep does not support customized installation.  
  
2. Copy the contents of the included “scripts” folder to C:\Scripts on the virtual machine.  
  
3. Prepare a sysprep answer file by modifying the following lines in Sysprep.xml. (Note: These lines are marked with a “!” before them.) You can use these as a template, or make your own and copy over the \<FirstLogonCommands\> section.  
  
   - $(OLDCOMPUTERNAME) Replace with the current computer name of the virtual machine.  
  
   - User accounts  
  
   - Passwords  
  
   - Any company details should also be updated in UpdateSqlServerAndInstance.cmd and your Sysprep.xml.  
  
     Alternatively, you can create a Sysprep answer file from scratch using use the [Automated Installation Kit (AIK)](http://www.microsoft.com/downloads/details.aspx?FamilyID=94bb6e34-d890-4932-81a5-5b50c657de08&DisplayLang=en) on Windows Server 2008. Ensure that your \<FirstLogonCommands\> section matches the samples so the BizTalk scripts will run on the first boot.  
  
#### To run Sysprep  
  
1. Open a command prompt and run Sysprep. The command will look something like:  
  
   ```  
   C:\windows\system32\sysprep\sysprep.exe /oobe /generalize /shutdown /unattend:c:\scripts\unattend_Win2K8x64.xml  
   ```  
  
2. Sysprep takes about half an hour to run. When it is complete, it will automatically shut down the virtual machine.  
  
3. After the virtual machine has been shut down, merge any snapshots, and copy your VHD file to a safe location.  
  
4. Your VHD is now ready to be deployed on other virtual machines, complete with operating system, BizTalk Server, and all prerequisites.  
  
   **SetupCompletecmd.txt**  
  
```  
del /Q /F c:\windows\system32\sysprep\sysprep.xml  
SqlCmd -s . -d Repository -A -Q "drop login [PDC08-CSD\Administrator]"  
SqlCmd -s . -d Repository -A -Q "create login [$(COMPUTERNAME)\Administrator] from windows"  
SqlCmd -s . -d Repository -A -Q "EXEC sp_changedbowner [$(COMPUTERNAME)\Administrator]"  
  
```  
  
 **Sysprep.xml**  
  
```  
- <!--   
References:  
"Unattended Installation Settings Reference" @ http://technet.microsoft.com/library/cc749204.aspx  
"How to Sysprep in Windows 2008 " @ http://briandesmond.com/blog/how-to-sysprep-in-windows-2008  
  
Make sure to modify the values specified for the   
<Credentials> and <DomainAccounts> sections of this unattend file.  
  
SetupComplete.cmd should be copied to the C:\Windows\Setup\Scripts\ folder before running sysprep.  
Contents of SetupComplete.cmd:  
  
del /Q /F c:\windows\system32\sysprep\sysprep.xml   
SqlCmd -s . -d Repository -A -Q "drop login [PDC08-CSD\Administrator]"  
SqlCmd -s . -d Repository -A -Q "create login [$(COMPUTERNAME)\Administrator] from windows"  
SqlCmd -s . -d Repository -A -Q "EXEC sp_changedbowner [$(COMPUTERNAME)\Administrator]"  
  
Sysprep.xml (this file) should be copied to the C:\Windows\System32\sysprep\ folder.  
  
Run sysprep with the following options:  
  
sysprep /generalize /oobe /shutdown /unattend:sysprep.xml  
  -->   
  <?xml version="1.0" encoding="utf-8" ?>   
- <unattend xmlns="urn:schemas-microsoft-com:unattend">  
- <settings pass="oobeSystem">  
- <component name="Microsoft-Windows-International-Core" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <InputLocale>0409:00000409</InputLocale>   
  <SystemLocale>en-US</SystemLocale>   
  <UILanguage>en-US</UILanguage>   
  <UILanguageFallback>en-US</UILanguageFallback>   
  <UserLocale>en-US</UserLocale>   
  </component>  
- <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <UserAccounts>  
- <!--   
This sets the password for the Administrator account back to pass@word1   
  -->   
- <AdministratorPassword>  
  <Value>pass@word1</Value>   
  <PlainText>true</PlainText>   
  </AdministratorPassword>  
- <!--   
Enter the appropriate value for the <Name> and <Domain> elements here,   
this group/account will be added to the local Administrators and Remote Desktop Users groups.  
  -->   
- <DomainAccounts>  
- <DomainAccountList wcm:action="add">  
- <DomainAccount wcm:action="add">  
  <Name>MSMQ4TR</Name>   
  <Group>Administrators;RemoteDesktopUsers</Group>   
  </DomainAccount>  
  <Domain>Northamerica.corp.microsoft.com</Domain>   
  </DomainAccountList>  
- <!--   
Additional DomainAccountList section. Uncomment/modify this section if you need to add   
groups / users from multiple domains to the local Administrators and Remote Desktop Users groups.  
                    <DomainAccountList wcm:action="add">  
                        <DomainAccount wcm:action="add">  
                            <Name>OsloVM_NTDev</Name>  
                            <Group>Administrators;RemoteDesktopUsers</Group>  
                        </DomainAccount>  
                        <Domain>Ntdev.corp.microsoft.com</Domain>  
                    </DomainAccountList>  
  -->   
  </DomainAccounts>  
  </UserAccounts>  
- <!--   
The new computer name is generated using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******.  
  -->   
  <RegisteredOwner>OsloVPC</RegisteredOwner>   
  <TimeZone>Pacific Standard Time</TimeZone>   
- <Display>  
  <ColorDepth>16</ColorDepth>   
  <HorizontalResolution>1024</HorizontalResolution>   
  <VerticalResolution>768</VerticalResolution>   
  </Display>  
  <RegisteredOrganization />   
  <StartPanelOff>true</StartPanelOff>   
  <ShowWindowsLive>false</ShowWindowsLive>   
  <DoNotCleanTaskBar>true</DoNotCleanTaskBar>   
  <DisableAutoDaylightTimeSet>false</DisableAutoDaylightTimeSet>   
  <BluetoothTaskbarIconEnabled>false</BluetoothTaskbarIconEnabled>   
- <VisualEffects>  
  <FontSmoothing>ClearType</FontSmoothing>   
  </VisualEffects>  
  </component>  
  </settings>  
- <settings pass="specialize">  
- <component name="Microsoft-Windows-IE-ESC" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <IEHardenAdmin>false</IEHardenAdmin>   
  <IEHardenUser>false</IEHardenUser>   
  </component>  
- <component name="Microsoft-Windows-UnattendedJoin" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <!--   
Enter credentials for a user account that has permissions to join a computer to the domain specified in the <JoinDomain> element. (Note: you must enter your password in plaintext here. This file will be deleted at the conclusion of Windows setup by SetupComplete.cmd in the C:\Windows\Setup\Scripts\ folder. For more information see the bottom of "How to Sysprep in Windows 2008" @ http://briandesmond.com/blog/how-to-sysprep-in-windows-2008)  
  -->   
- <Identification>  
- <Credentials>  
  <Domain>northamerica</Domain>   
  <Username>davidhamilton</Username>   
  <Password>******</Password>   
  </Credentials>  
  <JoinDomain>Redmond.corp.microsoft.com</JoinDomain>   
  </Identification>  
  </component>  
- <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
- <!--   
By specifying a value of "*" for <ComputerName>, Windows setup will generate a new computer name using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******  
  -->   
  <ComputerName>*</ComputerName>   
  <RegisteredOrganization />   
- <!--   
The new computer name is generated using a combination of <RegisteredOwner>, <RegisteredOrganization>, and random alphanumeric characters. Since <RegisteredOrganization> is blank, the new computer name will be OsloVPC-*******.   
  -->   
  <RegisteredOwner>OsloVPC</RegisteredOwner>   
  <ShowWindowsLive>false</ShowWindowsLive>   
  <BluetoothTaskbarIconEnabled>false</BluetoothTaskbarIconEnabled>   
- <!--   
This setting will copy the profile of the original image to the renamed image when set to true   
  -->   
  <CopyProfile>true</CopyProfile>   
  <DisableAutoDaylightTimeSet>false</DisableAutoDaylightTimeSet>   
  <DoNotCleanTaskBar>true</DoNotCleanTaskBar>   
  </component>  
  </settings>  
- <settings pass="generalize">  
- <component name="Microsoft-Windows-Security-Licensing-SLC" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <SkipRearm>1</SkipRearm>   
  </component>  
- <component name="Microsoft-Windows-OutOfBoxExperience" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <DoNotOpenInitialConfigurationTasksAtLogon>true</DoNotOpenInitialConfigurationTasksAtLogon>   
  </component>  
- <component name="Microsoft-Windows-ServerManager-SvrMgrNc" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <DoNotOpenServerManagerAtLogon>true</DoNotOpenServerManagerAtLogon>   
  </component>  
  </settings>  
  <cpi:offlineImage cpi:source="catalog:e:/sources/install_windows longhorn serverenterprise.clg" xmlns:cpi="urn:schemas-microsoft-com:cpi" />   
  </unattend>  
- <!--   
When the virtual machine is started, Windows setup will:  
  
 - Assign the copy a random computer name: "OsloVPC-*****"  
 - Reset the local Administrators password to pass@word1  
 - Join the domain specified in the sysprep.xml file (under Microsoft-Windows-UnattendedJoin\Identification\JoinDomain)  
 - Add the groups/users specified under <DomainAccounts> to the local Administrators and the local Remote Desktop Users group.  
  
Known issues:  
  
 - Sysprep removes the Server Manager icon from the Quick Launch toolbar, investigating how to prevent this.  
 - To start SQL Server Management Studio, either connect to the new server name (OsloVPC-*******) or else connect to ".".  The "Server name:" drop-down box in SQL Server Management Studio is pre-populated with "PDC08-CSD" which will not work since the computer name has been changed by sysprep.  
 - There are some known issues associated with changing the computer name; renaming the computer after everything was installed was not a design, development or test requirement for this milestone.  
  -->  
```  
  
## Comments  
 These scripts do not modify Microsoft Office SharePoint Server. If you are using the Windows SharePoint Services adapter, you will probably need to reconfigure Microsoft Office SharePoint Server and then update the SharePointAdapterManagementGroup key under HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\TPM.