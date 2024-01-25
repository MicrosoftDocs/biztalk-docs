---
description: "Learn more about: Known Issues with EDI Migration"
title: "Known Issues with EDI Migration"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Known Issues with EDI Migration
This topic describes known issues with migration from the EDI/HIPAA adapter model in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to BizTalk Server.  
  
## Credential Information Not Migrated for a FILE Send Port  
 When migrating a send port using the FILE transport type, the credentials used to access the file folder when the host does not have access to the network share will not be migrated. After migration, you will need to manually enable credentials, and enter the user name and password to be used, on the **Authentication** page of the **FILE Transport Properties** dialog box.  
  
## See Also  
 [Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md)   
 [EDI Migration Utilities](../core/edi-migration-utilities.md)
