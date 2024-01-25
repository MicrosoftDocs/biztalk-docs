---
description: "Learn more about: Export the Encryption Key"
title: "Export the Encryption Key"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Export the Encryption Key
If you are migrating from Host Integration Server 2000, you must export the encryption key. The encryption key is a security device that Host Integration Server 2000 uses to encrypt user passwords. It must be backed up because the migration utility will need it as part of the migration process.  
  
### To export the encryption key  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  Locate the Host Integration Server 2000 installation directory.  
  
3.  Type `udbkey /showkey >hostseckey.bak` to back up the key into a file.  
  
4.  Protect the file securely.  
  
## See Also  
 [Upgrading from Host Integration Server 2000 or SNA Server 4.0](../esso/upgrading-from-host-integration-server-2000-or-sna-server-4-0.md)
