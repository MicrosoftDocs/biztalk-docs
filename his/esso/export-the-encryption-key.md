---
title: "Export the Encryption Key | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 304f68a9-5e85-4640-a1b7-79e2d6182e6a
caps.latest.revision: 3
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