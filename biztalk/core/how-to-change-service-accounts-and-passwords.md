---
title: "How to Change Service Accounts and Passwords | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dff53d6b-c262-4b66-b822-1c61f54ae105
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Change Service Accounts and Passwords
After you configure BizTalk Server, it is common for organizations to require changing service accounts or passwords by Account policies, such as Password Policy and Account Lockout Policy. For more information about Account policies, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=62172](http://go.microsoft.com/fwlink/?LinkId=62172).  
  
 When changing service accounts or passwords, you must do the following:  
  
1. Create a new service account or change the password of existing accounts.  
  
2. Ensure that the service account is a member of the necessary Windows groups. For information about the local or domain groups to which you must add the service account, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
   > [!NOTE]
   >  In a domain group environment, you use the Active Directory Users and Computers console. In a local group environment, you use the Computer Management console.  
  
3. Do the following tasks depending on the type of service account.  
  
   |Service or Account|How to change user accounts|Required tasks after changing user accounts|How to change passwords|Required tasks after changing passwords|  
   |------------------------|---------------------------------|-------------------------------------------------|-----------------------------|---------------------------------------------|  
   |Enterprise Single Sign-On Service on Master Secret Server|1.  Ensure that you have a backup of the master secret. For more information, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).<br />2.  Change the service account using the Services console.<br />3.  Restore the master secret. For more information, see [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md).|Restart the service|Change the password of the account using the Services console.|Restart the service|  
   |Enterprise Single Sign-On Service|Change the service account using the Services console.|Restart the service|Change the password of the account using the Services console.|Restart the service|  
   |BizTalk Host Instance|Change the service account using the BizTalk Server Administration console|Restart the BizTalk host instance.|Change the password of the account using the BizTalk Server Administration console or Services console.|Restart the BizTalk host instance|  
   |BizTalk Isolated Host Instance and the corresponding application pool hosting SOAP receive adapter|1.  Change the service account using the BizTalk Server Administration console<br />2.  Change the account for the application pool using the IIS Management console **Note:**  The service account for the application pool should match the service account for a corresponding isolated host.|1.  Change the service account of the corresponding application pool using the IIS Management console.<br />2.  Restart the application pool using the IIS Management console.|Change the password of the account under which the application pool runs. using the IIS Management console **Note:**  You don't need to change the password in the BizTalk Server Administration console after changing password.|1.  Change the password of the account under which the corresponding application pool runs using the IIS Management console.<br />2.  Restart the application pool using the IIS Management console.|  
   |Rule Engine Update Service|Change the service account using the Configuration Manager or Services console.<br /><br /> Configuration Manager automatically restarts the service.|If you use Services console, you must manually restart the service.|Change the password of the account using Configuration Manager or Services console.<br /><br /> Configuration Manager automatically restarts the service.|If you use the Services console, you must manually restart the service.|  
   |BAM Notification Service|1.  Add the new account to SQL server where BAM Notification Service was installed.<br />2.  Grant the privileges to the new account. For more information about the required privileges, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)<br />3.  Change the service account using the Services console.|Restart the service|Change the password of the account using the Services Console|Restart the service|  
   |BAM Management Web Service|1.  Add the new account to the appropriate SQL server and grant the privileges in [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).<br />2.  Change the user account using the Configuration Manager.||Change the password of the user account using the Configuration Manager.||  
   |BAM Application Pool|Change the service account for the application pool using the Configuration Manager.<br /><br /> Configuration Manager automatically recycles the application pool.||Change the password of the account using the Configuration Manager.<br /><br /> Configuration Manager automatically recycles the application pool.||  
  
   The following procedure describes how to change service accounts and passwords using the Configuration Manager.  
  
### To change service accounts and passwords using Configuration Manager  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
2. In the **Microsoft BizTalk Server Configuration**, click **View**, click **Service Accounts**, and then change service accounts and passwords in the **Service Accounts** dialog box. For more information about Configuration Manager, see [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).  
  
   > [!NOTE]
   >  The Configuration Manager does not provide a centralized place to control over multiple computers. If you install Microsoft BizTalk Server on multiple computers, you have to change service accounts and passwords on each runtime computer.  
  
## See Also  
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md)   
 [Best Practices for Managing Windows Groups and User Accounts](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)   
 [Managing Hosts and Service Accounts](../core/managing-hosts-and-service-accounts.md)