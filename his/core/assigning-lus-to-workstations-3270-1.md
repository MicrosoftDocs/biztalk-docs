---
description: "Learn more about: Assigning LUs to Workstations (3270)"
title: "Assigning LUs to Workstations (3270)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Assigning LUs to Workstations (3270)
LUs and LU pools can also be assigned to workstations rather than users, effectively locking LUs to a specific machine. Assigning LUs to a workstation makes it easier for users to find and access different resources. For example, 200 hospital employees can share 50 workstations, each of which has a printer attached. Employees may want to access any of the 50 workstations and 50 printers. Instead of assigning 50 printer LUs to a pool and making the pool available to each user, each of the workstations can be added to Host Integration Server and a printer LU can be assigned to each workstation. Now, when a user logs onto any of the 50 workstations, the printer that is attached to the workstation will be available in the list of LUs.  
  
## See Also  
 [LU Pools (3270)](../core/lu-pools-3270-1.md)   
 [Providing Hot Backup and Load Balancing (3270)](../core/providing-hot-backup-and-load-balancing-3270-1.md)   
 [Deployment Strategies (3270)](../core/deployment-strategies-3270-1.md)
