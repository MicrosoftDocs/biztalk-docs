---
title: "How to Configure Navigation Between Distributed Activities | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f8faf0a-eb06-4383-932d-4106306d6cf3
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Navigation Between Distributed Activities
Distributed navigation allows users to view activities that exist in remote BAM deployments. When you enable distributed navigation, users of the BAM portal on one computer will be able to view activities in the BAM portal on another deployment of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 The procedure in this topic describes how to enable distributed navigation in the following scenario:  
  
- A sales department with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployed on computer 1.  
  
- A shipping department with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployed on computer 2.  
  
- A view called myBusinessView with an activity called Sales Data deployed on computer 1.  
  
- A view called myBusinessView with an activity called Shipping Data installed on computer 2.  
  
- A business user in the sales department with a business need to see the activities on both computers.  
  
### How to set up distributed navigation for remote activities  
  
1.  The administrator of computer 1 grants the business user access to the myBusinessView view on computer 1. You use the bm.exe command, as follows: **add-account -AccountName:\<account name\> -View:** myBusinessView  
  
2.  The administrator on computer 1 enables distributed navigation by running the enable reference command, as follows: **bm.exe enable-reference -TargetServer:** computer2 **-TargetDatabase:\<target database\>**  
  
    > [!NOTE]
    >  Typically the account used between departments for BAM Web services access will be different on different computers. Therefore, in this scenario the administrator of computer 1 must add the Web services Impersonation account of computer 1 to the BAM_ManagementWS role of the BAM Primary Import database for computer 2. For more information, see "Viewing and Modifying Role Memberships" at [http://go.microsoft.com/fwlink/?LinkId=66990](http://go.microsoft.com/fwlink/?LinkId=66990).  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
3.  The administrator of computer 2 grants the business user access to the myBusinessView view on computer 2 using the BM.exe command as noted in step 1.  
  
## Results of Setting Up Distributed Navigation  
 When distributed navigation is enabled the users added to the views on both computers will see the activities for the views deployed on both computers in the My Views pane of their home portal. When these users click an activity that is hosted on a remote deployment, they are seamlessly directed to the portal on which that activity is hosted and they are able to view the activity as if it were on their default portal.  
  
> [!NOTE]
>  Distributed navigation can be enabled in both directions. Following the procedure above on both computers that are sharing remote activities enables business users of the portals on either computer to use distributed navigation.  
  
## See Also  
 [Managing Distributed Navigation of Remote Activities](../core/managing-distributed-navigation-of-remote-activities.md)   
 [BAM Portal](../core/bam-portal.md)