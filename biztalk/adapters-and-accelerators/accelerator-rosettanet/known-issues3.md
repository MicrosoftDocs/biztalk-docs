---
title: "Known Issues with the RosettaNet accelerator in BizTalk Server | Microsoft Docs"
description: See known issues and resolutions with 0A1 notification of failure, BAM, installation and configuration, and more in BTARN in BizTalk Server
caps.latest.revision: 11
author: "MandiOhlinger"
manager: "anneta"

ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 335eb3c9-b565-470f-b69c-2a771ef8b476
ms.author: "mandia"
---

# Known Issues for Microsoft BizTalk Accelerator for RosettaNet (BTARN)
This section contains useful information that may help you avoid errors with Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. The known issues are grouped into the following areas:  
  
-   0A1 Notification of Failure  
  
-   Business Activity Monitoring (BAM)  
  
-   Installation and Configuration  
  
-   Miscellaneous  
  
## 0A1 Notification of Failure  
  
### BTARN does not perform cross-field validation for the CIDX process-configuration property and the 0A1 agreement property  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not prevent you from setting the "Standard" property for a process configuration profile to "CIDX", after you have set the "0A1 agreement" property for an agreement using that profile to "0A1", even though a CIDX does not support 0A1 agreements.  
  
## Business Activity Monitoring  
  
### Duplicate column data appears in the Business Activity Monitoring reports  
 The ActivityID and PIPInstanceID columns in the BAM activities Web reports contain the same content. This data accurately reflects the Partner Interface Process (PIP) instance identifier. The ActivityID uses this value for internal correlation. You can ignore this message.  
  
### Empty data columns in the Business Activity Monitoring Web reports  
 The Business Activity Monitoring (BAM) Web reports do not contain any data for 0A1 message processes. The 0A1 message columns in the Web reports are hard-coded with "Initiated 0A1".  
  
## Installation and Configuration  
  
### Groups and users in either the BizTalk Application Users group and the BizTalk Server Administrators group must be in the same domain  
 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] supports adding a group to either the BizTalk Application Users group or BizTalk Server Administrators group. However, individual user accounts and groups that belong to either the BizTalk Application Users group or the BizTalk Server Administrators group must be a part of the same domain.  
  
### Uninstallation of BTARN fails if BizTalk Server is removed first  
 If you remove BizTalk Server before removing [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] removal process fails without errors. To resolve this issue, re-install and reconfigure BizTalk Server and then remove [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
### Distributed deployment requires a domain controller  
 Deploying [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] in a multi-server environment requires a domain controller, for example, when you have installed [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] on one server and the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] databases used for configuration on another server.  
  
### Custom PIP configurations are not supported  
 The current release of [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support configuring PIPs with custom elements or other non-RosettaNet standard information.  
  
### BTARN automatically starts the Single Sign-On service  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] automatically starts the Single Sign-On (SSO) in an event when [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] requires it and the SSO service is not running.  
  
### The configuration program will not remove BTARN virtual directories from the excluded paths list when WebApps is not configured for the default Web site  
 If you unconfigure a [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] installation in which the Web application virtual folder was configured to be SharePoint Server, not Default Web Site, after unconfiguration you will have to manually remove the btarnapp and btarnhttpreceive virtual directories from the Excluded Paths list in the SharePoint Central Administration site. This occurs because when you configure the Web application virtual folder to be SharePoint Server, you have to manually add btarnapp and btarnhttpreceive to the Excluded Paths list. The configuration program will not be able to automatically remove them from the Excluded Paths list.  
  
## Miscellaneous  
  
### BTARN will receive messages encrypted in either encryption algorithm  
 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline receives and decrypts a message even if the protocol that is used to encrypt the message and the Encoding setting in this field do not match. Therefore, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receives messages that are encrypted in either RC2-40 or 3DES.  
  
### BTARN requires a signal in a single-action synchronous scenario  
 In a single-action synchronous scenario, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] always expects and generates signals. This behavior is different from the RosettaNet specification that a signal may or may not be required in a single-action synchronous scenario. If [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] is a responder, it always generates a signal in response to a message from the initiator. If [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] is an initiator, it always expects a signal back from the responder. If [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not receive a signal, it times out after the interval specified in the `Time To Perform` property in the process configuration settings, and it generates a 0A1 message.  
  
### BTARN supports UTF-16 in received messages  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receives and processes messages that have a character set of UTF-16. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sends messages with a character set of UTF-8.  
  
### Namespaces must be stripped from response messages mapped from request messages  
 If you use BizTalk Mapper in the private process of a double-action scenario, BizTalk Mapper adds namespaces to some element tags in response message instances mapped from request messages. These namespaces cause a failure in the send pipeline. You must remove these namespaces. Use the HeaderHelper sample to do this. For more information, see [Double Action PIPAutomation Orchestration &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md) and [Step 4: Creating the HeaderHelper Project &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md).  
  
### Changing URI settings requires IISRESET  
 While running the Setup program, you set the URI settings that the receive and send .aspx pages use and the URI settings of the receive and send adapters. You must change these settings if you change the name of the computer that the .aspx pages or the adapters are installed on. You can change these settings by re-running the configuration process, but this requires resetting all configuration settings. You can change the URI settings alone by changing the associated registry keys (`AsyncReceivePortURI`, `RNIFSenderURI`, and `SyncReceivePortURI`). After changing any one of these registry settings, you must run IISRESET for the changes to take effect. This is because [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] caches the settings for its use. After running IISRESET, you must also restart BizTalk services.  
  
### BTARN does not enforce restrictions on RNIF v1.1 enumerations  
 The RosettaNet Implementation Framework (RNIF) Specification v1.1 specifies restrictions on some RNIF schema enumerations. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not enforce these restrictions, and does not validate against those restrictions. The restrictions do not apply to RNIF v2.01.  
  
 This is true for the following service header elements:  
  
-   `GlobalBusinessActionCode`  
  
-   `GlobalPartnerClassificationCode`  
  
-   `GlobalBusinessServiceCode`  
  
-   `GlobalProcessCode`  
  
-   `GlobalProcessIndicatorCode`  
  
-   `VersionIdentifier`  
  
### PerformanceControlRequest parameters will not override default process configuration settings  
 Incoming messages can contain `PerformanceControlRequest` parameters in the service header. These parameters include values for the time delay parameters of Time to Acknowledge (Receipt) and Time to Perform, as set in the process configuration settings made in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not dynamically set the time delays based on the `PerformanceControlRequest` parameters in the incoming message. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] always takes the time delays from the default PIP values set in the process configuration settings. This follows the RosettaNet Implementation Framework (RNIF) Specification v1.1.  
  
### The PIP name and PIP version of double-action messages are case-sensitive  
 If the PIP name and PIP version of a response message have a different case than the corresponding values of the original double-action request message, the initiator [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] rejects the response message as not valid and returns an exception to the responder.  
  
### BTARN does not support changing agreement settings while there are active processes  
 Changes to agreement properties will apply as soon as you click **Apply** or **OK** to accept them. After you change an agreement, any new activity in an already running process or any new process involving that agreement will use the changed agreement properties. If there was a process running when you changed the agreement, it may have already used the previous agreement properties for a message. The new messages for that process will use the new agreement settings, which may generate unpredictable results. It is recommended that you change agreement settings when there are no processes running.  
  
### BTARN will not perform cross-field validation after changes to a process configuration profile  
 When you create a process configuration profile and then create an agreement, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] performs cross-field validation to make sure that the properties of the agreement and the profile are compatible. For example, it checks that for a profile with the Standard property set to "CIDX", the 0A1 agreement property of the agreement is set to "No 0A1". However, if you change a process configuration profile after having created an agreement, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not perform cross-field validation. If you change the Standard property from "RosettaNet" to "CIDX", [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not verify that the 0A1 agreement property of the agreement is set to "No 0A1".  
  
### Errors will result if all orchestrations are not started  
 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs nine orchestrations. For [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] to process messages successfully, you must bind, enlist, and start all nine of these orchestrations before initiating processing. For more information, see the "Orchestration Management in BizTalk Explorer" or "Managing Orchestrations" topics in BizTalk Server Help.  
  
### RNIFReceive.aspx does not remove the MIME bottom boundary from a message  
 When the RNIFReceive.aspx page receives a message from an RNIFSend.aspx page of a partner, the message includes a MIME header, and a MIME top and bottom boundary, a base 64 number. RNIFSend.aspx adds the header and boundaries to the message for RNIF transmission. RNIFReceive.aspx should remove the MIME header and boundaries from the message before submitting the message to the public process. RNIFReceive.aspx removes the MIME header and the upper boundary, but it does not remove the bottom boundary. The presence of the bottom boundary does not affect processing of the message in the public process.  
  
### BTARN does not support a case-sensitive configuration of SQL Server databases  
 If you make [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] databases and database objects case-sensitive, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console cannot find database resources and throws an exception. The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] databases and database objects must be case-insensitive.  
  
### All queries in database maintenance scripts should be written for UTC time  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] databases use UTC (Universal Time Coordinate) time, so that any query that you create to maintain one of these databases must be written for UTC time. For example, if your maintenance script were to use the `GetDate()` command, you should change it to `GetUTCDate()`.  
  
### A PublicResponder orchestration will reject a duplicate request action message  
 When a `PublicResponder` orchestration (PublicResponderV11.odx) receives a duplicate request action message, it will log a warning in the event log, and then reject the message. If a duplicate message is received after the responder orchestration has completed, BizTalk Server will stop the message because there are no subscriptions.  
  
### Transmission errors will not be shown in BAM if the public process has stopped  
 If a transmission error occurs when a public-process orchestration processes its final message, the event log and HAT display the error, but BAM does not. BAM cannot display the message because the orchestration has stopped.  
  
### The pipeline.exe tool cannot be used to debug a BTARN receive pipeline  
 If you want to debug a receive pipeline, you have to create a port hosting the pipeline. You cannot debug it using the pipeline.exe tool that BizTalk Server provides.  
  
### An error may be generated for a retried message that is successfully processed after the orchestration finishes  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses orchestrations to represent process flow. In some cases, in which several retried messages are retried, the orchestration may finish successfully before a retried message arrives in the BizTalk MessageBox. When this behavior occurs, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] generates a corresponding "completed but discarded" error message. You should look at your line-of-business (LOB) application to determine whether the process has finished or not. If the LOB application indicates successful completion, you can ignore the "completed but discarded" message.  
  
### An XML file exported from tracking.xls may have incorrect fields  
 When you define new tracking views in a tracking XLS file, and export an XML file from the tracking XLS file, some of the field names will be slightly modified. To correct this, verify the fields in your customized tracking XML file against the standard tracking.xml field installed by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup.  
  
### RNIF 1.1 service header schema for signals and responses may need modification  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ships all RosettaNet header schemas out of the box. Some implementations use the Signal Control and Action Control nodes differently than others, as described below.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] out of the box ships the Signal Control element as below. Note that the same may be true for the Action Control element.  
  
```  
<!ELEMENT SignalControl (  
          InstanceIdentifier,  
          PartnerRoute,  
          SignalIdentity,  
          inResponseTo)>  
```  
  
 If your solution requires this sequence, then you do not need to do anything.  
  
 Some other implementations, on the other hand, use the following code:  
  
```  
<!ELEMENT SignalControl (  
          inResponseTo,  
          InstanceIdentifier,  
          PartnerRoute,  
          SignalIdentity)>  
```  
  
 If your solution requires this sequence, refer to KB 889523. This software update will change the corresponding XML schema. Note that this update only affects RNIF 1.1 processes.  
  
### PipAutomationGetAction SQL stored procedure needs update  
 You need to update the PipAutomationGetAction SQL stored procedure to lock single records. Delete the following lines:  
  
```  
IF @@ERROR <> 0  
    UPDATE MessagesToLOB SET Delivered = -1 WHERE MessageID = @tempGUID  
```  
  
 The correct PipAutomationGetAction stored procedure is as follows:  
  
```  
CREATE PROCEDURE PipAutomationGetAction  
AS  
 SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
BEGIN TRANSACTION  
DECLARE @tempGUID nvarchar(36)  
SELECT TOP 1 @tempGUID = MessageID FROM MessagesToLOB WITH (READPAST,UPDLOCK,ROWLOCK)  
   WHERE Delivered = 0 AND MessageCategory = 10  
  ORDER BY TimeCreated  
  SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion, ServiceContent FROM MessagesToLOB  
   WHERE MessageID = @tempGUID  
For xml auto  
UPDATE MessagesToLOB SET Delivered = 1 WHERE MessageID = @tempGUID  
 COMMIT TRANSACTION  
GO  
```  
  
### You can customize aspx code to return the error description  
 If you need to log or send an error description, you can customize the aspx code to have the actual text returned in the response. To do so, use HttpResponse.Status (which is the intrinsic asp request’s response object) or HttpWebResponse.StatusDescription (which is returned by the [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] call to the HttpWebRequest object’s GetResponse method). To return the return values from one of the applicable response objects, set the Response.Status value similar to how Response.StatusCode is set in the aspx code that ships with [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
### RNIF 1.1 messages cannot be read in plain text from non-repudiation tables if the encoding method is set to Base64  
 This only happens if the encoding method is set to Base64. Messages can be read in clear text from non-repudiation tables if encoding method is set to quoted-printable or 8-bit. You need to save the message file with *.eml extension and then open it using Outlook Express to read the message and Outlook Express will decode the message for you. You may also use the code below to read the Base64 encoded messages from non-repudiation tables.  
  
```  
byte[] textBytes = Convert.FromBase64String(txtEncodedText.Text);  
string plainText = Encoding.UTF8.GetString(textBytes);  
txtOutput.Text = plainText;  
```  
  
## See Also  
[Troubleshooting and known issues](troubleshooting-and-known-issues-in-rosettanet.md)