---
title: "Windows Accounts for a Secure Distributed BizTalk Server Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Server, Windows groups"
  - "user accounts, naming conventions"
  - "user accounts"
  - "access control, Windows groups"
  - "security, access control"
  - "architecture, security"
  - "security, Windows accounts"
  - "administrator accounts"
  - "user accounts, administrators"
  - "architecture, large distributions"
ms.assetid: 2a0893ef-8bfb-481b-b024-7f7d6e2a6f09
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows Accounts for a Secure Distributed BizTalk Server Deployment
For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).  
  
 This section provides recommendations for creating Windows groups and accounts in a distributed BizTalk Server environment. The group and account names are suggestions based on the function of the groups and accounts. You can choose the name of these groups and accounts. For more information about distributed BizTalk Server architectures, see [Large Distributed Architecture](../core/large-distributed-architecture.md).  
  
## Windows Groups for a Secure Distributed BizTalk Server Deployment  
 The following list describes the recommended Windows groups for the domain administrator to create in the domain controller in the data tier.  
  
- SSO Administrators  
  
- SSO Affiliate Administrators  
  
- BizTalk Server Administrators  
  
- BizTalk Server Operators  
  
  For complete information about the Windows groups that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
  In addition to the previous domain groups, the following table lists additional groups specific to secure deployment for the domain administrator to create in the domain controller in the data tier.  
  
|Group name (suggested)|Purpose|  
|------------------------------|-------------|  
|BizTalk Processing Host Users 1|Group for the host instances of a specific in-process host that you use for processing messages. Create a group for each in-process host that you use for processing messages in your BizTalk Server environment.|  
|BizTalk Send Host Users 1|Group for the host instance of a specific in-process host that you use for sending messages. Create a group for each in-process host that you use for sending messages in your BizTalk Server environment.|  
|BizTalk Receive Host Users 1|Group for the host instance of a specific in-process host that you use for receiving messages. Create a group for each in-process host that you use for receiving messages in your BizTalk Server environment.|  
|BizTalk Tracking Host Users|Group for the BizTalk host that you dedicate for tracking.|  
|BizTalk SOAP Users|Group for the host instances of the isolated host you use for the SOAP adapter.|  
|BizTalk HTTP Users|Group for the host instances of the isolated hosts you use for the HTTP adapter.|  
  
 The domain administrator must create the following groups in the domain controller of the service interfaces domain:  
  
-   BizTalk BAM Portal Users  
  
## Windows User or Service Accounts for a Secure Distributed BizTalk Server Deployment  
 The following table lists the recommended accounts for the domain administrator to create in the domain controller of the data domain. The domain administrator must ensure the accounts are members of the groups indicated.  
  
 For complete information about the user accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
|Account name (example)|Type|Member of group|  
|------------------------------|----------|---------------------|  
|SSO administrator|User|SSO Administrators|  
|SSO service|Service|SSO Administrators|  
|SSO master secret|Service|SSO Administrators|  
|BizTalk administrator|User|BizTalk Administrators<br /><br /> SSO Affiliate Administrators|  
|BizTalk operator|User|BizTalk Operators|  
|BizTalk Processing 1|Service|BizTalk Processing Host Users 1|  
|BizTalk Processing 2 **Note:**  You can create multiple accounts for each processing host in your environment.|Service|BizTalk Processing Host Users 1|  
|BizTalk Tracking|Service|BizTalk Tracking Host Users|  
|SOAP adapter|Service|BizTalk SOAP Users|  
|HTTP adapter|Service|BizTalk HTTP Users|  
|Rule Engine Update Service|Service||  
|Installation|User|SSO Administrators (only for configuring the master secret server)<br /><br /> local Administrators<br /><br /> sysadmin SQL Server Role<br /><br /> OLAP Administrator|  
|BAM Application pool|Service|IIS_WPG|  
|BAM Management|Service|IIS_WPG|  
|BAM Notification|Service|SQLServer2005NotificationServicesUser$\<**ComputerName**\>|  
  
 The following table lists the recommended accounts for the domain administrator to create in the domain controller of the corporate domain.  
  
|Account name|Type|  
|------------------|----------|  
|SharePoint administrator|User|  
|SharePoint Site credential|User|  
  
## See Also  
 [Large Distributed Architecture](../core/large-distributed-architecture.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md)