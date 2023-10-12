---
description: "Learn more about: How to Manage the BizTalk Server Administrators Group"
title: "How to Manage the BizTalk Server Administrators Group"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Manage the BizTalk Server Administrators Group
The BizTalk Server Administrators group has the fewest privileges necessary to perform administrative tasks. You add users to the BizTalk Server Administrators group so that they can perform administrative tasks by using the BizTalk Server Administration Console or the WMI provider. You also remove users from the BizTalk Server Administrators group when they no longer need to perform administrative tasks by using the BizTalk Server Administration Console or the WMI provider.  
  
## Prerequisites  
 You must be a member of the Administrators or Domain Admins group to perform this procedure.  
  
### To add users to the local BizTalk Server Administrators group  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Computer Management**.  
  
2.  Expand **System Tools**, expand **Local Users and Groups**, and then click the **Groups** folder. The folder contents appear in the details pane.  
  
3.  In the details pane, click **BizTalk Server Administrators**.  
  
4.  On the **Action** menu, point to **All Tasks**, and then click **Add to Group**.  
  
5.  In the **BizTalk Server Administrators Properties** dialog box, click **Add**.  
  
6.  In the **Look in** list, select your domain or computer name.  
  
7.  In the list that contains the users and computers associated with the domain or computer you selected in step 6, select the user account to add, click **Add**, and then click **OK**.  
  
8.  Click **OK** to close the **BizTalk Server Administrators Properties** dialog box.  
  
### To remove users from local the BizTalk Server Administrators group  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Computer Management**.  
  
2.  Expand **System Tools**, expand **Local Users and Groups**, and then click the **Groups** folder. The folder contents appear in the details pane.  
  
3.  In the details pane, click **BizTalk Server Administrators**.  
  
4.  On the **Action** menu, click **Properties**.  
  
5.  In the **BizTalk Server Administrators Properties** dialog box, select the user account you want to remove, and then click **Remove**.  
  
6.  Click **OK**.  
  
### To add users to the domain BizTalk Server Administrators group  
  
1.  Log on to the domain controller where the SQL Server databases are joined by using the Domain Admins account.  
  
2.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.  
  
    1.  In the console tree, click the folder that contains the BizTalk Server Administrators group to which you want to add a member.  
  
    2.  In the details pane, right-click the BizTalk Server Administrators group, and then click **Properties**.  
  
    3.  On the **Members** tab, click **Add**.  
  
    4.  In **Enter the object names to select**, type the name of the user, and then click **OK**.  
  
### To remove users from the domain BizTalk Server Administrators group  
  
1.  Log on to the domain controller where SQL databases are joined using the Domain Admins account.  
  
2.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.  
  
    1.  In the console tree, click the folder that contains the BizTalk Server Administrators group to which you want to add a member.  
  
    2.  In the details pane, right-click the BizTalk Server Administrators group, and then click **Properties**.  
  
    3.  On the **Members** tab, click the member you want to remove, and then click **Remove**.  
  
    4.  Click **OK**.  
  
## See Also  
 [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md)   
 [Managing Hosts and Service Accounts](../core/managing-hosts-and-service-accounts.md)   
 [Best Practices for Managing Windows Groups and User Accounts](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Managing Windows Groups and User Accounts](../core/managing-windows-groups-and-user-accounts.md)
