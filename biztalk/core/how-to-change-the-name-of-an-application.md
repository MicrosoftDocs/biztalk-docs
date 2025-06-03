---
description: "Learn more about: How to Change the Name of an Application"
title: "How to Change the Name of an Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Change the Name of an Application
This topic describes how to use the BizTalk Server Administration console to change the name of an application. The application name that you use cannot already exist in the group.  
  
> [!NOTE]
>  If you have exported an .msi file for an application that has a reference to the renamed application, the reference will no longer function when you import the .msi file. You will need to update the reference with the new application name.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To change the name of an application  
  
1. Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand  **BizTalk Server Administration**, right-click the application whose name you want to change, and click **Properties**.  
  
3. In the **Name** box, type a new name for the application, and then click **OK**.  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)
