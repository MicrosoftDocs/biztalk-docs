---
description: "Learn more about: How to Associate 3270 Printer LUs with 3270 Display LUs"
title: "How to Associate 3270 Printer LUs with 3270 Display LUs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d5d9353-e147-47c3-8452-e156ad8f068e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Associate 3270 Printer LUs with 3270 Display LUs
Users who have host applications with direct relationships between display LUs and printer LUs can associate printers with the LUs.  
  
 You can associate a printer LU with a display LU. This feature is designed to support specialized host applications that have hard-coded associations between display LUs and printer LUs. When a 3270 display LU is configured to have an associated printer and then subsequently assigned to a user or group, users will see both the display LU and a special printer LU named ASSOCPRT. When users connect to the display LU, they can then open the ASSOCPRT LU, which [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] maps to the defined associated printer LU.  
  
 You can also add display LUs with associated printer LUs to LU pools. The LU pools can then be assigned to users and groups.  
  
 When multiple display LUs are assigned to users, the order in which the resources are opened is important. If all of the display LUs have associated printers, the user should alternate opening displays and ASSOCPRTs. If some of the display LUs do not have associated printers, use a naming convention so the user can determine the display LUs that have associated printers from those that do not.  
  
### To associate printer LUs to display LUs  
  
1.  In the Host Integration Server console tree, click **Pools**.  
  
2.  Right-click the display LU that you want to associate with a printer, and click **Properties**.  
  
3.  Click the **Associated Printer** tab.  
  
4.  In the **Associated Printer LU** box, select the printer that you want to associate, and then click **OK**.  
  
5.  Repeat steps 2 through 4 for each display LU that you want to associate with a printer LU.  
  
6.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  Printer LUs are available to any users or groups that have been assigned the corresponding display LUs.  
  
> [!NOTE]
>  Associated printer LUs are assigned a generic placeholder name of *ASSOCPRT*.  
  
## See Also  
 [How to Assign LUs to Workstations](../core/how-to-assign-lus-to-workstations1.md)   
 [Creating and Configuring LUs](../core/creating-and-configuring-lus1.md)
