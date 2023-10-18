---
description: "Learn more about: Distributed System Problems"
title: "Distributed System Problems"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Distributed System Problems
In a distributed destination system the restore jobs are not aware of errors or problems on the other computers. For example, suppose that computer A is restoring the BizTalk Management database and the BizTalk Tracking database, and computer B is restoring the BizTalk MessageBox database. Both computers successfully restore backup sets 1 through 25. Set 26, however, has a corrupted log backup file of the BizTalk MessageBox database. Computer A restores its databases correctly but computer B fails to restore the corrupted file.  
  
 In this situation, force a full backup on the source system. Continuing the example above, assume that the problem was diagnosed and a full backup was created for set 35. Computer A then restores sets 26 to 34, because it is not aware of the problem on Computer B. Computer B will fail until it sees full backup set 35 and subsequent log backup set 36 (remember that there must always be one subsequent complete log backup for a set to be restored). When sets 35 and 36 arrive on computer B, it will repair itself using 35. After the repair is complete, computer A and B will be in sync.  
  
## See Also  
 [Troubleshooting Log Shipping](../technical-guides/troubleshooting-log-shipping.md)
