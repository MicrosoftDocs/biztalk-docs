---
title: "Troubleshooting: Issues and Resolutions3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting"
ms.assetid: 40f59f54-183e-43db-afb5-0a45b437697f
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting: Issues and Resolutions
This topic addresses issues related to running [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. The individual issues detail a specific symptom, a possible cause, and a solution.  
  
## Error publishing a batch of "n" messages  
  
### Symptom  
 You receive the following or similar error in the event log:  
  
 The Messaging Engine encountered an error publishing a batch of "n" messages to the Message Box database for the transport adapter "BizTalk HTTP Receiver". Please refer to Health and Activity Tracking tool for more detailed information on this failure and check the endpoint bindings are correctly configured.  
  
### Possible Cause  
 This error could be caused by one of the following reasons:  
  
- Missing decryption certificate  
  
- Incorrectly encrypted message  
  
- Unauthorized message (source not recognized as a valid partner)  
  
- Message failing validation of any header part: preamble, delivery header, or service header.  
  
  This message may be preceded by another error message that details the cause.  
  
### Solution  
 Review the details provided with the error message for additional help. Restarting [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™ may resolve this issue.  
  
## You cannot unenlist all artifacts  
  
### Symptom  
 Running the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean utility does not unenlist all artifacts.  
  
### Possible Cause  
 If you run the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean utility before deleting agreements and partners from the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Management Console (MMC), the BtarnClean utility will not be able to unenlist all artifacts because they are still used.  
  
### Solution  
  
##### To remove artifacts using the Loopback utility  
  
1.  At the command prompt, type:  
  
    ```  
    lookback.exe /disable <home org or partner>  
    ```  
  
2.  Run the BtarnClean.exe file.  
  
3.  In BizTalk Explorer, delete the parties.  
  
## Installing BTARN on a computer without BizTalk Server causes missing files  
  
### Symptom  
 Running the ConfigFramework.exe file yields no results on a computer that does not have [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server or [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installed. You can only use this [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration as an HTTP client.  
  
### Possible Cause  
 Two DLL files are missing from the installation.  
  
### Solution  
 Install SQLXML on the computer, and then manually copy the Msxml4.dll and Atl71.dll files to the System folder.  
  
## You receive an access error when attempting to change the BTARN configuration  
  
### Symptom  
 You receive the following error message when you import a configuration file using the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console:  
  
 Could not store transport type data for Primary Transport of Send Port 'RNSTT.Async' to config store. Access is denied.  
  
 You can also receive this error when you try to change the configuration, such as by creating a new partner.  
  
### Possible Cause  
 The current user is not a member of the BizTalk Administrators group.  
  
### Solution  
 Make sure that the current user is a member of the BizTalk Administrators group.  
  
## You receive BAM errors  
  
### Symptom  
 You receive the following error messages in the Event Viewer:  
  
 Error happened in tracking Message activity. Error message is Stored Procedure Does Not Exist.  
  
 -or-  
  
 Error in terminating BAM message activity with id *\<ID number\>*.  
  
### Possible Cause  
 The Business Activity Monitoring (BAM) tracking tool is not installed.  
  
### Solution  
 Install the BAM tracking tool using the **Custom Installation** option. If you do not need BAM functionality, you can ignore these messages or disable tracking using the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console. After you disable tracking, you must restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Internet and Information Services (IIS).  
  
## Your XSD Schema does not display properly in BizTalk Editor  
  
### Symptom  
 You cannot view the content of a schema properly in BizTalk Editor.  
  
### Possible Cause  
 The schema is missing the `displayroot_reference` attribute for the `schemaInfo` element.  
  
### Solution  
 Open the schema in Notepad or another text editor and add the `displayroot_reference` attribute to the `schemaInfo` element. The value of the `displayroot_reference` attribute should be the same as the `root_reference` attribute.  
  
 For example:  
  
 \<schemaInfo document_type="4A1" version="V02_00" xmlns="<http://schemas.microsoft.com/BizTalk/2003>" *displayroot_reference="Pip4A1StrategicForecastNotification"* root_reference="Pip4A1StrategicForecastNotification" \>  
  
## 404 Not found error when sending a HTTP request  
  
### Symptom  
 You receive the following or similar errors when sending a HTTP request:  
  
 The remote server returned an error: (404) Not Found.  
  
 Message cannot be sent to ../BTSHttpReceive.dll.  
  
### Possible Cause  
 The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Internet Server API (ISAPI) extension DLL (BTSHttpReceive.dll) has not been configured in Internet Information Services (IIS). This occurs if the HwsMessages HttpReceive web service extension is not configured and if this web service extension is configured, but not allowed.  
  
### Solution  
 To determine whether the HwsMessages HttpReceive web service extension is configured, and if it is not configured, to allow it, perform the following procedure.  
  
##### To configure the BizTalk ISAPI extension DLL in IIS  
  
1. Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2. Expand **\<computer name\> (local computer)**, and then click **Web Service Extensions**.  
  
3. In the **Web Service Extension** pane, verify that the status for HwsMessages HttpReceive is Allowed. If not, right-click **HwsMessages HttpReceive**, and then click **Allow**.  
  
   If the HwsMessages HttpReceive web service extension is not configured (it is not included in the Web Service Extensions list in IIS Manager), perform the following procedure.  
  
##### To configure the BizTalk ISAPI extension DLL in IIS  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  Expand **\<computer name\> (local computer)**, right-click **Web Service Extensions**, and then click **Add a new Web service extension**.  
  
3.  In the **New Web Service Extension** dialog box, in the **Extension Name** box, type **BizTalk ISAPI Extension**, and then click **Add**.  
  
4.  In the **Add File** dialog box, in the **Path to file** box, type **\<drive\>:\Program Files\Microsoft BizTalk Server \<version\>\HttpReceive\BTSHttpReceive.dll**, and then click **OK**.  
  
5.  In the **New Web Service Extension** dialog box, select **Set extension status to Allowed**, and then click **OK**.  
  
## An access violation occurs when running the Configuration Wizard  
  
### Symptom  
 You receive the following or similar error in the event log:  
  
 A BizTalk isolated host instance configured with the user account '\HostSvc' was either not running or does not exist on this computer. Use the BizTalk Administration Console to create a new isolated host or reconfigure an existing to run as '\hostsvc'.  
  
### Possible Cause  
 To run the Configuration Wizard, the user should be configured as '\<*machine name*\>\hostsvc', not '\hostsvc'.  
  
### Solution  
 Open the BizTalk Administration Console, and change hosts that are running under the account '\hostsvc', so that they run under the account '\<*machine name*\>\hostsvc'.  
  
## You receive an error when importing and compiling a RosettaNet Next Generation PIP schema  
  
### Symptom  
 You receive the following or similar error in the event log:  
  
 error CS0234: The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'RosettaNet.Schemas.System' (are you missing an assembly reference?).  
  
### Possible Cause  
 One of your schemas, for example, StandardDocumentHeader.xsd, has a [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] namespace of RosettaNet.Schemas.System.  
  
### Solution  
 Remove the "System" from the [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] namespace for the schema, so that the namespace is RosettaNet.Schemas.  
  
## You receive an error when trying to manually deploy the BAM Package  
  
### Symptom  
 When you manually try to deploy the BAM package for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], you receive an error indicating that you cannot deploy the package.  
  
### Possible Cause  
 The DTS packages BAM_DM_Process and BAM_DM_Message are installed on your system, preventing deployment of the BAM package.  
  
### Solution  
  
##### To recover from the error condition and deploy the BAM package  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **Enterprise Manager**.  
  
2.  In Enterprise Manager, expand **Microsoft SQL Servers**, **SQL Server Group**, **(local) (Windows NT)**, and **Data Transformation Services**.  
  
3.  Click **Local Packages**, right-click **BAM_DM_Message**, and then click **Delete**.  
  
4.  Right-click **BAM_DM_Process**, and then click **Delete**.  
  
5.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
6.  At the command prompt, type the following code to deploy the tracking file, and then click **OK**.  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server <version>\Tracking  
    bm deploy all  "%ProgramFiles%\Microsoft BizTalk <version> Accelerator for RosettaNet\BAMTracking\tracking.xml"  
    ```  
  
## You receive an error when adding a new PIP  
  
### Symptom  
 You receive the following or similar error in the event log:  
  
 UNP.SCON.VALERR: A failure occurred while validating the service content.  
  
 Details: Finding document specification by message type failed. Verify that the schema is deployed properly.  
  
### Possible Cause  
 Either the document namespace or the root node property the deployed schema for the instance Pip4A5NotifyofForecastReply is incorrect.  
  
### Solution  
 Verify that the document namespace and the root node property for the deployed schema for instance Pip4A5NotifyofForecastReply is correct.  
  
## Error during the configuration of BTARN at installation time, caused by presumed network connectivity issues  
  
### Symptom  
 During the configuration process, you receive an error in the error dialog box indicating that the computer is not properly connected to the network, when in fact it is.  
  
### Possible Cause  
 This error may be caused by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration program misinterpreting IP addresses. The hosts file in C:\Windows\system32\drivers\etc contains an entry mapping the localhost host name to the IP address 127.0.0.1. The configuration program may confuse this value with the loopback address, and assume that the computer is not connected properly to the network.  
  
### Solution  
  
##### To avoid this error and complete the configuration process  
  
1. In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Windows\system32\drivers\etc, and open the hosts file using Notepad.  
  
2. Comment out the line "127.0.0.1        localhost" by placing "# " at the start of the line. Save the changed hosts file.  
  
3. Click **Retry** in the error dialog box.  
  
4. After configuration has completed successfully, re-open the hosts file in Notepad, remove the comment mark at the start of the line mapping localhost, and then save the hosts file.  
  
## You receive an error regarding incorrect signature length  
  
### Symptom  
 You receive the following or similar error in the event log:  
  
 There was a failure executing the receive pipeline: "Microsoft.Solutions.BTARN.Pipelines.Receive" Source: "MIME/SMIME decoder" Receive Location: "/BTARNHttpReceive/BTSHTTPReceive.dll?xRNResponseType=async" Reason: Incorrect signature length, value = 1935897193.  
  
### Possible Cause  
 This error message indicates that the signature length is incorrect. In addition to the above cause, this error could also due to the incorrect or incomplete header content length which leads to the wrong bytes read on the signature length.  
  
### Solution  
 Verify that both of the signature length and header content length is correct.  
  
## You receive "503: Service Unavailable" from Internet Explorer on 64-bit machine  
  
### Symptom  
 After [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] configuration is completed, when you try to access [http://localhost](http://localhost/) or [http://localhost/BtarnApp/RnifSend.aspx](http://localhost/BtarnApp/RnifSend.aspx), you may receive the following or similar error:  
  
 503: Service Unavailable  
  
### Possible Cause  
 This error may be caused by the ISAPI filter found under C:\windows\system32\rpcproxy\rpcproxy.dll being set on IIS Web Sites.  
  
### Solution  
  
##### To remove RpcProxy filter entry in IIS  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  Expand **\<computer name\> (local computer)**, right-click **Web Sites**, and then click **Properties**.  
  
3.  Select **ISAPI Filters** tab.  
  
4.  Select **RpcProxy filter**, and click **Remove**.  
  
5.  Click **OK**.  
  
6.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
7.  At the command prompt, type the following code to reset IIS.  
  
    ```  
    iisreset  
    ```  
  
> [!NOTE]
>  If you try to access http://localhost or http://localhost/BtarnApp/RnifSend.aspx again after performing the above steps, you will receive HTTP 400 message back from the Internet Explorer which means that IIS is now functioning properly.  
  
## The HubScenario sample will not be installed correctly if the assembly key files are not entered for the projects  
  
### Symptom  
 When you run setup.bat in *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\HubScenario to set up the HubScenario sample, the operation fails.  
  
### Possible Cause  
 The HubScenario and HubHelper assemblies were not deployed correctly because the assembly key files were not set in the projects.  
  
### Solution  
 Set the assembly key files for the HubScenario and HubHelper projects. For more information, see [HubScenario Sample](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md).  
  
## Run setupx64.bat to set up the Double Action PIPAutomation Orchestration sample on SQL Server 2008 R2/2008 SP1  
  
### Symptom  
 When you run setup.bat to build and initialize the Double Action PIPAutomation Orchestration sample, the PipAutomationGetAction stored procedure in the BTARNData database is not created.  
  
### Possible Cause  
 You ran setup.bat on a 64-bit computer or on a BizTalk Server installation that is running on SQL Server 2008 R2/2008 SP1. Both of these instances require you to run setupx64.bat.  
  
### Solution  
 Run setupx64.bat to create the stored procedure. For more information, see [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).  
  
## Enable the BTARN Application Pools for 32 bit on Windows Server 2008, 64-bit Windows Operating System (OS)  
 To run the BTARN End to End scenario on Windows Server 2008,64-bit Windows Operating System (OS), Internet Information Services Manager 7.5/7.0.  
  
 1. Enable the BTARN Application Pools for 32 bit.  
  
 2. Add a HTTP Handler for *.dll refering the IsapiModule Filters.  
  
## See Also  
 [BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md)   
 [Loopback](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)