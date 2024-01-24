---
description: "Learn more about: Configuring and Viewing Audit Logs"
title: "Configuring and Viewing Audit Logs"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring and Viewing Audit Logs
The ESB Management Portal maintains an audit log of actions that help you to monitor usage and track problems. Administrators can specify which events the portal will write to the audit log.  
  
### To view the audit logs for the portal  
  
1.  Point to the **Admin** tab on the portal main menu, and then click **Manage Audit Log** to open the [Audit Log Page](../esb-toolkit/audit-log-page.md).  
  
2.  To see the resubmission details and the original message for resubmitted messages, click the identifier of a message in the list to open the Audit Log – Message Viewer page.  
  
### To configure the auditing settings for the portal  
  
1.  Ensure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group (of which portal administrators are automatically a member).  
  
2.  Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).  
  
3.  To change the auditing options, select the check boxes in the **AuditOptions** section for each event you want to audit. The available events are the saving of modified settings, successful resubmission of a fault after editing, and failure when resubmitting a fault.
