---
description: "Learn more about: Host Groups"
title: "Host Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d92478b-b3a2-4c5a-925e-5495ee481e82
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Host Groups

## Overview
The host group is the Windows group (named the BizTalk Application Users group by default) that you use for accounts with access to the in-process BizTalk hosts (host processes in BizTalk Server). It is recommended that you use one host group for each in-process host in your environment.  
  
 You can only associate a host with one Windows group (called a *host group*). The host group must have a SQL Server login and privileges in all relevant BizTalk Server databases. When you associate a host with the host group, you grant the host the privileges of the host group.  
  
 If you use the Configuration Wizard to create hosts, and you specify a local Windows group to use for hosts, the Configuration Wizard automatically creates two Windows groups. The default names of these groups are the BizTalk Application Users group and the BizTalk Isolated Host Users group.  
  
 When you create a host instance of a host associated with the host group, the host instance inherits the database privileges of the host group.  
  
 The host group is a property of the host Windows Management Instrumentation (WMI) object. You can change the Windows group that a host belongs to if there are no host instances of the host.  
  
 You specify the host group a host belongs to when you create the host. The BizTalk WMI provider grants the privileges that the host group has (for example, the BizTalk Server privileges required for runtime functionality, including SQL Server logins and database user access) to the host. You must specify the correct service account (host) when you create a host instance, so that the BizTalk Server WMI provider grants the privileges of the host group to the host instance.  
  
> [!NOTE]
>  If you want to create a local host group, you can create a local Windows group and assign a domain user as a member of the group. If you specify a local Windows group for the Host, the Windows group member, whether it is a domain or local user, can be used as the host instance log-on user.  

## Required permissions  
 The host group requires the following privileges:  
  
-   It must be a member of the BTS_HOST_USERS SQL Server role in the following databases:  
  
    -   BizTalk Management 
  
    -   MessageBox  
  
    -   Rule Engine  
  
    -   Tracking  
  
    -   BAM Primary Import  
  
-   It must be a member of the BTS_\<in-process host name\>_USERS SQL Server role for the MessageBox database  
  
-   It must be a member of the BAM_EVENT_WRITER SQL Server role in the BAM Primary Import database.  
  
> [!NOTE]
>  If you designate a host as a tracking host, BizTalk Server Administration automatically removes the BizTalk Host group from the SQL Server roles for the Tracking database. You must manually remove the BizTalk Host group from the SQL Server roles for the BizTalk Management database and the MessageBox database. For information about designating a host as a tracking host, see [Modify Host Properties](../core/how-to-modify-host-properties.md).  
  
## See Also  
 [Entities](../core/entities.md)
