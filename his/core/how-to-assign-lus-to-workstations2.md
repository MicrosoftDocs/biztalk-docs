---
title: "How to Assign LUs to Workstations2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e80c229-2cba-4ffd-96d1-2c0fbb4c45b9
caps.latest.revision: 4
---
# How to Assign LUs to Workstations
You can assign LUs to a workstation rather than a user, which makes it possible to lock LUs to a particular workstation. Assigning an LU to a workstation makes it easier for users to find and access different resources. For example, it makes it easier for a user at a workstation to use a printer located near the workstation, instead of one assigned to the user.  
  
 With this feature, you can insert a workstation object and define it by specifying parameters such as IP address, workstation name, and others. You can then assign 3270 display and printer LUs to the workstation. These LUs will be accessible to any users connecting from those workstations. The LUs do not need to be specifically assigned to the user.  
  
 For example, 200 hospital users share 50 workstations and 50 printers. Users may want to use any of the 50 workstations and 50 printers. They can log on to any of the 50 workstations and print using the printer attached to that workstation. Instead of assigning all 50 printers to 200 user accounts, the administrator can add the 50 workstations to [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] and assign a printer LU to each workstation. When a user logs on to any of the 50 workstations, the printer attached to that workstation will be available in the list of LUs.  
  
 You can also configure a workstation so that it will only allow the use of those LUs assigned to the workstation, regardless of the user who is logged on. You can assign LUs to workstations in the same manner that LUs are assigned to users.  
  
 For example, if the workstation is flagged for restricted access, a user cannot gain unauthorized access to other LUs regardless of the user ID and password that is used. This feature enhances network security.  
  
### To assign LUs to workstations  
  
1.  In the Host Integration Server console tree, right-click **Workstations**, point to **New**, and then click **Workstation**.  
  
2.  Fill in the **Workstation Properties** dialog box.  
  
3.  Click **OK** to add the new workstation.  
  
4.  To assign LUs to the workstation, click **Connections**, and then click the connection that contains the LUs.  
  
5.  Right-click the LU that you want to assign, and click **Assign to Workstation**.  
  
6.  Click the workstation, and click **OK**.  
  
7.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  All workstation users must be members of the same SNA subdomain. You can avoid having to add each user to the subdomain by assigning the **Everyone** group to the subdomain and assigning no LUs to the group.  
  
## See Also  
 [How to Associate 3270 Printer LUs with 3270 Display LUs](../core/how-to-associate-3270-printer-lus-with-3270-display-lus1.md)   
 [Creating and Configuring LUs](../core/creating-and-configuring-lus2.md)