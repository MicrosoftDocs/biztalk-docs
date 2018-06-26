---
title: "Best Practices for Securing Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters, security"
  - "best practices, adapters"
  - "adapters, permissions"
  - "security, adapters"
  - "permissions, adapters"
  - "best practices, security"
  - "adapters, best practices"
ms.assetid: 004e1a01-b316-4eee-967f-5a806431de2b
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Securing Adapters
This topic provides a list of best practices for adapter security.  
  
 **Do not install untrusted adapters on your computer; use only certified adapter development partners.**  
  
 **Do not store sensitive customer data in the default adapter schema.**  
  
 You should configure the user name and password information only after you deploy an adapter. This ensures that the information gets stored in the SSO database. For more information about the SSO database, see [Using SSO](../core/using-sso.md).  
  
 **Grant the following permissions on the shared folders (the Receive folder and Send folder) that are used to pick up and drop files using the File and EDI adapters:**  
  
- **Receive  folder**  
  
   The receive folder for the File adapter is configurable on the receive location. The receive folder for the EDI adapter is configurable on the receive handler. The service account for the BizTalk Host that picks up the file should have the following permissions at the file-system level:  
  
  - List Folder / Read Data  
  
  - Delete SubFolder and Files  
  
    If the receive folder is on a network share, the following permissions must be granted at the file-share level:  
  
  - The service account for the BizTalk Host that picks up the file must have Full Control permissions.  
  
  - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrators must have Full Control permissions for troubleshooting.  
  
  - The external user or programs that drop files to this location must have Write permissions.  
  
- **Send folder**  
  
   The send folder for the File and EDI adapters are configurable on the send port.  
  
  - The service account for the BizTalk Host or Hosts that drop files here must have Write permissions.  
  
  - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrators must have Full Control permissions.  
  
  - The external user or program that picks up files must have Read permissions.  
  
  **Add the user account under which the EDI service is running to the BTS_HOST_USERS SQL role.**  
  
  This is required so that you can obtain BizTalk Explorer Object Management (OM) Access without administrative permissions. To do this, add "EDI Subsystem Users" to the BTS_HOST_USERS role in the BizTalk Management database, BizTalkMgmtDb.  
  
  To add "EDI Subsystem Users" to the BTS_HOST_USERS role on SQL Server 2005, complete the following steps:  
  
1. Launch SQL Server Management Studio from **Start, Programs, Microsoft SQL Server 2008**.  
  
2. Connect to the SQL Server that houses your BizTalk Management database.  
  
3. Expand this server in the Object Explorer.  
  
4. Expand **Databases**, and then expand the BizTalk Management database.  
  
5. Expand **Security**, expand **Roles**, and then click to select **Database Roles**  
  
6. In the details pane, right-click the BTS_HOST_USERS role, and then click **Properties**.  
  
7. In the BTS_HOST_USERS dialog box, click **Add**, click **Browse**, and then check the box next to the EDI Subsystem Users group to add it.  
  
    If the EDI Subsystem Users group is not available in the list of users to add, you must add the EDI Subsystem Users group as a new database user to the BizTalk Management database. To add the EDI Subsystem Users group as a new database user, complete the following steps in SQL Server Management Studio:  
  
   1.  Expand the BizTalk Management database.  
  
   2.  Expand **Security**.  
  
   3.  Right-click **Users** and click **New User**.  
  
   4.  Click the ellipses (…) button next to the text box for **Login name** to display the **Select Login** dialog box.  
  
   5.  Click the Browse button, enter the **EDI Subsystem Users** group, and then click **OK.** If prompted with the **Multiple Objects Found** dialog box, select the **EDI Subsystem Users** login and click **OK**.  
  
   6.  On the **Database User - New** dialog box enter **EDI Subsystem Users** for the **User name** textbox and click **OK**.  
  
   **Add the user account under which the BizTalk service is running to the EDI Subsystem Users group.**  
  
   Follow these steps to add the user account for the BizTalk service to the EDI Subsystem Users group.  
  
-   **If BizTalk Server is configured to use domain groups:**  
  
    1.  Logon to a Windows Server computer in the domain.  
  
    2.  Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Active Directory Users and Computers**.  
  
        > [!NOTE]
        >  You must have appropriate domain level permissions to modify objects in the **Active Directory Users and Computers** interface.  
  
    3.  Click to expand the domain container and click to expand the **Users** container.  
  
    4.  Double click the **EDI Subsystem Users** group to display the properties for this group.  
  
    5.  Click the **Members** tab of the **EDI Subsystem Users** group dialog.  
  
    6.  Click the **Add** button to add the user account for the BizTalk Service to this group.  
  
    7.  Click **OK**.  
  
-   **If BizTalk Server is configured to use local groups:**  
  
    1.  Logon to the BizTalk Server.  
  
    2.  Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **Computer Management**.  
  
    3.  Click to expand **System Tools**, click to expand **Local Users and Groups**, and click to expand **Groups**.  
  
    4.  Double click the **EDI Subsystem Users** group to display the properties for this group.  
  
    5.  Click the **Add** button to add the user account for the BizTalk service to this group.  
  
    6.  Click **OK**.