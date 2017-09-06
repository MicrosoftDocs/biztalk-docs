---
title: "Known Issues with EDI Migration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc5d0a7e-974d-4e3b-a406-412420779456
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with EDI Migration
This topic describes known issues with migration from the EDI/HIPAA adapter model in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## Credential Information Not Migrated for a FILE Send Port  
 When migrating a send port using the FILE transport type, the credentials used to access the file folder when the host does not have access to the network share will not be migrated. After migration, you will need to manually enable credentials, and enter the user name and password to be used, on the **Authentication** page of the **FILE Transport Properties** dialog box.  
  
## See Also  
 [Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md)   
 [EDI Migration Utilities](../core/edi-migration-utilities.md)