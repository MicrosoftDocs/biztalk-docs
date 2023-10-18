---
description: "Learn more about: Checklist: Performing Daily Maintenance Checks"
title: "Checklist: Performing Daily Maintenance Checks"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Checklist: Performing Daily Maintenance Checks

This topic describes some of the items that you should check on a daily basis to help monitor the status of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. You must perform most of these checks consistently and archive the results over a period of time to obtain the greatest benefit. We recommend that you automate routine maintenance checks whenever possible.

- Check for failed disks in the hardware RAID (reliability check). For more information, go to:

  - [Overview of Disk Management](/windows-server/storage/disk-management/overview-of-disk-management)
  - [Troubleshooting Disk Management](/windows-server/storage/disk-management/troubleshooting-disk-management)

- Check for messages requiring manual intervention such as suspended messages (reliability check). For information about manually checking for suspended messages, see [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md).

- Check for any errors or issues with the various databases associated with BizTalk Server, especially the MessageBox database.

  Run the BizTalk MsgBoxViewer tool available, which is included in the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md). This tool analyzes the BizTalk MessageBox and other databases and generates an HTML report containing warnings, if any and other information related to the databases.

  - You can also save the reports for later use. These reports might be useful when troubleshooting issues with the BizTalk application. 
  - Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.

- Resolve issues, if any, identified by the BizTalk MsgBoxViewer tool.

  Run the Terminator tool, which is included in the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md). This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool.

- Check the event logs for errors and warnings (administration check). BizTalk Server errors and warning events are saved in the application log. The event source is "BizTalk Server".

## See Also
 
- [Maintaining Reliability](../technical-guides/maintaining-reliability.md)
- [Monitoring BizTalk Server2](../technical-guides/monitoring-biztalk-server2.md)