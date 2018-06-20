---
title: "Known Issues with EDI and AS2 Status Reporting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d755dca-a4b6-44be-bc45-88c0b17685a0
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI and AS2 Status Reporting
This topic describes known issues with EDI status reporting in BizTalk Server.  
  
## Batch status reporting data may not be updated if the batch orchestration is stopped outside of the Partner Agreement Manager  
 A batch orchestration instance can be deactivated through the Batches page of the EDI Properties dialog box for a party. If you deactivate a batch orchestration instance that way, BizTalk Server will update the status reporting data for that batch. However, if you stop the batch orchestration in another way, for example, by stopping the orchestration from one of the query pages on the Group Overview page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, the status reporting data may not be updated, and you may end up with a batch status report that is out of date. For example, the status report could indicate that the batch is still active, even though the batch orchestration instance has been deactivated.  
  
## The BizTalk Service Needs to Be Restarted After EDI Status Reporting Has Been Enabled  
 **Symptom**  
  
 EDI status reporting has been enabled, but EDI status reports are not being generated.  
  
 **Possible Cause**  
  
 The BizTalk Service needs to be restarted after EDI status reporting has been activated or deactivated for the change to take effect. If the AS2EdiReceive or AS2EdiSend pipeline is being used in your solution, both the BizTalk Service and the IIS service need to be restarted for the change to take effect.  
  
 **Resolution**  
  
 Restart the BizTalk Service (in the Computer Management dialog box). If the AS2EdiReceive pipeline or the AS2EdiSend pipeline is being used in your solution, restart the IIS Admin service (using the *iisreset* command), as well.  
  
> [!NOTE]
>  Restarting the BizTalk Service or the IIS Admin service is not necessary when enabling AS2 status reporting.  
  
## The Status Report Will Display "9999" for the Year When the AS2 Message Date Time in the Message is a Null Value  
 If the AS2 Message Date Time field in an incoming AS2 message is set to Null, a value of “9999” will be shown for the year in the AS2 Message Date Time field for that message in the AS2 status report.  
  
 If the AS2 Message Date Time field in an incoming AS2 message cannot be parsed (such as Mon, 21 May 2007 10:08:28 NZST), the AS2 Message Date Time field for that message in the AS2 status report will be set to the current time.  
  
## Status Reporting Is Still Configured After BAM Tools Have Been Uninstalled  
 To install EDI Status Reporting, you must install BAM Tools. However, if you uninstall BAM Tools, Status Reporting will still be configured. This is by design.  
  
 After BAM Tools are removed, it will no longer be possible to search status reporting tables through the user interface. However, if status reporting is enabled, BizTalk Server will still create records in the status reporting tables.  
  
## Only One EDI Interchange Will Be Correlated to an AS2 Message in the Status Report UI  
 If an AS2 message contains multiple EDI interchanges, and you attempt to display the status of the multiple EDI interchanges in the AS2 message, only the last EDI interchange will be displayed in the Interchange/ACK status report. In addition, the **EDI Interchange Control No** field in the AS2/MDN Status report will only show the last interchange control number. (The interchange control number correlates the AS2 message and its EDI interchange payload.)  
  
 The data for all EDI interchanges in an AS2 message is saved in the status report database. You can display all interchanges in an AS2 message in the Interchange/ACK Status report if the **Control ID Equals All** clause is the status report query. This will also potentially display other interchanges that are not in the AS2 message; however, you can determine which EDI interchanges are in a single AS2 message by looking at other fields, such as the Sender party, Receiver party, and Interchange Date Time.  
  
## Removing the BAM Tools from a group will prevent you from viewing EDI or AS2 status reports  
 If you remove the BAM tools from a group, trying to view EDI or AS2 status reports will result in errors. One such error would indicate that the stored procedures bts_GetBatchStatusRecords is not found. If you get an error when trying to view EDI or AS2 status reports, verify that group, runtime, and BAM tools are configured correctly for EDI and AS2.  
  
 You can avoid this issue if you unconfigure BAM tools, rather than simply removing them. If you unconfigure BAM tools, you will be prompted to unconfigure the dependent EDI/AS2 feature. You are not prompted to do so if you remove the BAM tools.  
  
## Status reporting will not work after an upgrade if the BAM tools are not configured  
 For EDI and AS2 status reporting to work, the BAM tools must be configured. If you upgrade an installation of [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to a subsequent version, and do not configure the BAM tools in the upgrade process, EDI/AS2 status reporting functionality on the upgraded installation will not work correctly.  
  
 If you want to use status reporting after you upgrade to BizTalk Server, make sure that the BAM tools are configured before you perform the upgrade.  
  
 If status reporting does not work after you perform the upgrade, determine in the upgrade logs if the BAM tools were configured prior to upgrade. If not, you can configure the BAM tools and then deploy the BusinessMessageJournal BAM activity contained in the EdiStatusReportingActivityDefs.xml file in *\<drive\>*:\Program Files\Microsoft BizTalk Server.  
  
## Disabling transaction-set storage affects an activated batch, but enabling storage does not  
 If you disable the storage of transaction sets while an instance of the batching orchestration is activated, the change will take place immediately. BizTalk Server will store transaction sets for the batch while storage is enabled, but will not store transaction sets after storage has been disabled. You disable storage of transaction sets by clearing the "Store transaction set/payload for reporting" property in the General pane of the EDI Properties dialog box.  
  
 However, if you activate an instance of the batching orchestration while storage of transaction sets is disabled, and then enable that storage, no transaction sets will be stored for the batch that is being created.  
  
## UNICODE AS2 messages will not be displayed completely in text wire format  
 If BizTalk Server processes an AS2 message or an MDN that is encoded in UNICODE format, and you attempt to view the message in text wire format, BizTalk Server will not display the message completely. This occurs because the "00" byte of UNICODE format is interpreted as the end of the stream. However, if you attempt to view the message in binary wire format, BizTalk Server will display the message completely.  
  
 This occurs when status reporting is activated for AS2 messages (in the General pane of the AS2 Properties dialog box), and when storage of inbound or outbound AS2 or MDN messages is enabled (in the Party as AS2 Message Receiver pane or the Party as AS2 Message Sender pane of the AS2 Properties dialog box).  
  
## Enabling AS2 status reporting and send port body tracking simultaneously may cause an error  
 If you enable AS2 status reporting and send port body tracking simultaneously, the following error might be displayed in the Event Viewer: "The Messaging Engine encountered an error while deleting one or more messages." This occurs when the send port is a static solicit-response AS2 send port with AS2Send and AS2Receive pipelines. It occurs when the following properties are enabled:  
  
- The "Activate AS2 Reporting" property in the General pane of the AS2 Properties dialog box.  
  
- The "Store outbound encoded AS2 messages in non-repudiation database" property in the Party as AS2 Message Receiver pane of the AS2 Properties dialog box.  
  
- The "Request message after port processing" property in the Tracking pane of the Send Port Properties dialog box.  
  
  The workaround for this issue is to clear the "Store outbound encoded AS2 messages in non-repudiation database" property or the "Request message after port processing" property. We recommend that you disable "Request message after port processing" so that AS2 tracking can capture the body information along with other pieces of information for AS2 status reporting.  
  
## EDI and AS2 message context properties are not available after upgrading to BizTalk 2009  
 After upgrading to BizTalk Server, no context properties are displayed in status reporting for any EDI or AS2 messages received before the upgrade occurred.  Messages received after the upgrade will correctly display the context properties.  
  
 The EDI and AS2 context property collections were not stored as part of the message in previous versions of BizTalk Server and are unavailable after an upgrade. After upgrading to BizTalk Server, AS2 context properties are stored as part of the message, however EDI context properties are not.  
  
## Interchange date for received documents may display the wrong year in status reports  
 If a received document specified the date in YYMMDD format, BizTalk Server uses the following logic to determine the year value:  
  
- If YY is greater than or equal to 75, the year will be displayed as 19YY.  
  
- If YY is less than 75, the year will be displayed as 20YY.  
  
  For example, if the value of ISA09 of an incoming message contains 991113, the status report will display the date as 11/13/1999.  
  
## Error message may be displayed as a string of question marks.  
 In BizTalk Server localized builds, if an error message is displayed as a string of question marks, you need to change the system locale according to the Operating System language to get the expected error message. For more information on changing the system locale, see [Change the system locale](http://windows.microsoft.com/en-IN/windows-vista/Change-the-system-locale).  
  
## See Also  
 [Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md)   
 [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md)