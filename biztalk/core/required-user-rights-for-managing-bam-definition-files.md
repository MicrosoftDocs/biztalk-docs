---
title: "Required User Rights for Managing BAM Definition Files | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb4fb73f-b783-4a04-9bd6-a135b3dd2655
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Required User Rights for Managing BAM Definition Files
BAM definition files can be created, managed, and viewed by users in any role. Managing BAM definition files includes deploying and removing them as well as managing the activities, views, alerts, and artifacts that are associated with the definition file.  
  
 Administrators should maintain proper asset protection, such as creating shared folders with appropriate access permissions. When using the BAM Add-In for Excel, we recommend that users set the macro security level to high.  
  
 There are no required user rights needed to modify the BAM definition files (depending on permissions set on where the definition files are stored). Changes to definition files are not automatically applied to the BAM infrastructure. To apply the changes you must use the BAM Management utility.  
  
 To use the BAM Management utility, you must be an administrator on the computer to which the BAM definition is being applied or a member of the BizTalk Server Administrators group.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [What Is a BAM Definition?](../core/what-is-a-bam-definition.md)   
 [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md)