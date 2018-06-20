---
title: "Upgrading from Host Integration Server 2000 or SNA Server 4.0 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7bd636a9-cdad-4773-b3b8-d7904eab85f4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Upgrading from Host Integration Server 2000 or SNA Server 4.0
Older versions of Host Integration Server, such as Host Integration Server 2000 and SNA Server 4.0, provided both Single Sign-On and password synchronization through their host security feature. This feature was based around the host security domain, which contained user mappings to map credentials between Windows and host systems.  
  
 In [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], the Enterprise Single Sign-On (SSO) feature replaces host security as the source of Single Sign-On and password synchronization. Although some concepts are shared between the old and new features, there are important differences. In addition to the increased functionality, there are two primary conceptual differences in the new features:  
  
- Host security domains are replaced by affiliate applications.  
  
- Security credential data is now stored in a SQL Server database.  
  
  To migrate your existing host security data into the new SSO environment, use the Migration Utility. This is a command-line tool (hissomig.exe) that migrates all necessary data from the old version to the new, enabling you to continue using Single Sign-On without modifying your applications.  
  
  The topics in this section walk you through the migration process. It is important to follow these steps in the order given.  
  
## In This Section  
 [Back up the Existing Security Data](../esso/back-up-the-existing-security-data.md)  
  
 [Export the Encryption Key](../esso/export-the-encryption-key.md)  
  
 [Install Enterprise Single Sign-On](../esso/install-enterprise-single-sign-on.md)  
  
 [Copy the Migration Utility to the Master Secret Server](../esso/copy-the-migration-utility-to-the-master-secret-server.md)  
  
 [Run the Migration Utility](../esso/run-the-migration-utility.md)