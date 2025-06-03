---
description: "Learn more about: Setting Port Numbers (TN3270)"
title: "Setting Port Numbers (TN3270)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Setting Port Numbers (TN3270)
As with all TCP/IP services, TN3270 requires a free TCP port in which clients can locate the TN3270 service. By default, the TN3270 service defaults to port 23, the same port as standard Telnet services. Because no two services can share the same TCP port, it is recommended that you change the TN3270 service to use TCP port 24 or some other unused TCP port. When attempting to connect to the TN3270 service from a client application, you must also specify the new TCP port within the application connection settings.  
  
## See Also  
 [Deploying Hot Backup and Load Balancing (TN3270)](../core/deploying-hot-backup-and-load-balancing-tn3270-1.md)   
 [Assigning LUs to an IP Address (TN3270)](../core/assigning-lus-to-an-ip-address-tn3270-1.md)   
 [Deployment Strategies (TN3270)](../core/deployment-strategies-tn3270-2.md)
