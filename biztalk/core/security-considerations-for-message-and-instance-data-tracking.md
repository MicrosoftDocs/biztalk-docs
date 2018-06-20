---
title: "Security Considerations for Message and Instance Data Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "permissions, HAT"
  - "MessageBox database, HAT"
  - "Tracking database, HAT"
  - "security, HAT"
  - "HAT, permissions"
  - "HAT, security"
  - "Management database, HAT"
ms.assetid: 83e47dc2-c8e2-42a2-9c85-d511e7dae83f
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security Considerations for Message and Instance Data Tracking
For security reasons, message and service instance tracking does not use browsers or URLs as in previous releases of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This monitoring option is included as a part of the Group Overview page in the BizTalk Server Administration Console.  For backward compatibility, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] still hosts Microsoft Internet Explorer inside a shell for security reasons.  

 By tracking message and service instance data, you can access the technical details necessary to troubleshoot and optimize your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. Because this tracking data is powerful, you should limit access to it in your production environment so that malicious or unauthorized users do not cause damage. It is recommended you follow these guidelines for securing and using the BizTalk Server Administration Console in your environment.  

- You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group to view data using the BizTalk Server Administration Console. To access message bodies in the Group Overview section of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

   When you use message and service instance tracking, you can access the following databases:  


  |               Database               |                                                                                                   User Group/Permissions                                                                                                   |
  |--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |  BizTalk Management (BizTalkMgmtDb)  |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators               |
  | BizTalk MessageBox (BizTalkMsgBoxDb) | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators, or read-write permissions |
  |   BizTalk Tracking (BizTalkDTADb)    | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators, or read-only permissions  |


- Message and service instance tracking generates reports about all hosts in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment based on the parameters of a query. To minimize the potential of information disclosure, only members of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group can use the BizTalk Server Administration Console to execute these querries. However, if you do not want all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators to have access to the data this tracking process produces, you can limit their access to the data by adding/removing users from the HM_EVENT_WRITER and BAM_EVENT_WRITER SQL Server roles in the BizTalk Tracking (BizTalkDTADb) database.  

- BizTalk uses the BAM_EVENT_WRITER and HM_EVENT_WRITER SQL Server roles to grant/deny their members permissions to read/write the tracking data in the Tracking database, but not through role membership. Do not remove these SQL Server roles. When you change a host from hosting to not hosting tracking (or vice versa), the adm_ChangeHostTrackingPrivilege stored procedure is called. This stored procedure reads the definition of the BAM_EVENT_WRITER and HM_EVENT_WRITER SQL Server roles and apply the corresponding GRANT/DENY statements to the Host Windows group. This achieves the same effect as adding the Host Windows group to these SQL roles.  

- When you configure the BizTalk Server Administration Console preferences to view data from an archived database, In this case the tracking queries connect to the databases that hold the archived data, not to the currently active BizTalk Tracking (BizTalkDTADb) database.  

- You cannot debug live orchestrations across Network Address Translation (NAT) firewalls. You must have an administration computer on the Processing domain in order to debug live orchestrations.  

- Depending on how you configure tracking and the pipelines, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may store sensitive information contained in the message context. If you use WMI or tracking to save message bodies to a file location, ensure that the location has a strong discretionary access control list (DACL) so that only [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators have read permissions to these message bodies. Apply the same DACL to any location you save the message bodies, including non-BizTalk databases where you may archive and restore them.  

- You must manually grant permissions to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to access the Tracking Analysis Server (BizTalkAnalysisDb) database; by default, only OLAP administrators have permissions to it.  

## See Also  
 [Planning for Message and Instance Tracking](../core/planning-for-message-and-instance-tracking.md)   
 [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)