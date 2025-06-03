---
description: "Learn more about: How to Update the BAM Configuration Using the BAM Management Utility"
title: "How to Update the BAM Configuration Using the BAM Management Utility"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Update the BAM Configuration Using the BAM Management Utility
Administrators can use the BAM Management utility to update an existing BAM installation.  
  
## Prerequisites  
 You must have Administrator permissions on the BAM database being updated.  
  
### To update the BAM configuration using the BAM Management utility  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type the following at the command line prompt: **bm update-config -FileName:\<config file\>**, where \<*configuration file*\> is replaced by the name of your BAM configuration file. Press **ENTER**.  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
