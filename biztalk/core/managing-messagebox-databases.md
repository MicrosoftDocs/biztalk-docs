---
description: "Learn more about: Managing MessageBox Databases"
title: "Managing MessageBox Databases"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Managing MessageBox Databases
The MessageBox database has three essential functions. It stores subscriptions and tracking information and it delivers the messages to the services that match the subscriptions. The MessageBox database is a host platform that stores the queues and state tables for each BizTalk Host. The MessageBox database also stores messages and message properties.  
  
 If the MessageBox databases are an asset with high-risk exposure in your environment, we recommend that you use Internet Protocol security (IPSec) or Secure Sockets Layer (SSL) to restrict and secure communication to and from the MessageBox databases.  
  
 If you use Windows Server 2003, you must enable the distributed transaction coordinator (DTC) on the MessageBox database. You must also enable network clients for multicomputer deployments. For more information, see [Ports for the Administration Server](../core/ports-for-the-administration-server.md).  
  
 This section contains procedural information about managing MessageBox databases in your environment. For conceptual information about MessageBox databases and the subscription model Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to process messages, see [The MessageBox Database](../core/the-messagebox-database.md).  
  
## In This Section  
  
-   [How to Add a New MessageBox Database](../core/how-to-add-a-new-messagebox-database.md)  
  
-   [How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md)  
  
-   [How to Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md)
