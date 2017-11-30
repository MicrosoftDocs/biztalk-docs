---
title: "Checklist: Performing Daily Maintenance Checks | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1abae6fb-abce-4f23-a07d-b32ba58cd070
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Performing Daily Maintenance Checks
This topic describes some of the items that you should check on a daily basis to help monitor the status of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. You must perform most of these checks consistently and archive the results over a period of time to obtain the greatest benefit. We recommend that you automate routine maintenance checks whenever possible.  
  
|Steps|Reference|  
|-----------|---------------|  
|Check for failed disks in the hardware RAID (reliability check).|[Manage Disks](http://go.microsoft.com/fwlink/?LinkId=158666) (http://go.microsoft.com/fwlink/?LinkId=158666).|  
|Check for messages requiring manual intervention such as suspended messages (reliability check).|For information about manually checking for suspended messages, see [Investigating Orchestration, Port, and Message Failures](http://go.microsoft.com/fwlink/?LinkId=154512) (http://go.microsoft.com/fwlink/?LinkId=154512).|  
|Check for any errors or issues with the various databases associated with BizTalk Server, especially the MessageBox database.|Run the BizTalk MsgBoxViewer tool available from [BizTalk MsgBoxViewer - download here the latest version of the tool](http://go.microsoft.com/fwlink/?LinkId=151930) (http://go.microsoft.com/fwlink/?LinkId=151930). This tool analyzes the BizTalk MessageBox and other databases and generates an HTML report containing warnings, if any and other information related to the databases. **Tip:**  You can also save the reports for later use. These reports might be useful when troubleshooting issues with the BizTalk application. **Note:**  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.|  
|Resolve issues, if any, identified by the BizTalk MsgBoxViewer tool.|Run the Terminator tool available at [Terminator](http://go.microsoft.com/fwlink/?LinkId=151931) (http://go.microsoft.com/fwlink/?LinkId=151931). This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool. For more information about how the Terminator tool integrates with the BizTalk MsgBoxViewer tool, see [Using BizTalk Terminator to resolve issues identified by BizTalk MsgBoxViewer](http://go.microsoft.com/fwlink/?LinkId=151932) (http://go.microsoft.com/fwlink/?LinkId=151932). **Note:**  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.|  
|Check the event logs for errors and warnings (administration check).|BizTalk Server errors and warning events are saved in the application log. The event source is "BizTalk Server."|  
  
## See Also  
 [Maintaining Reliability](../technical-guides/maintaining-reliability.md)   
 [Monitoring BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md)