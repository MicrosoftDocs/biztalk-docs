---
title: "Install and Configure the Microsoft BizTalk ESB Toolkit | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 698843f7-8361-4d02-9278-0e66f2a9f472
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install and Configure the Microsoft BizTalk ESB Toolkit
Starting with BizTalk Server 2013 and new versions, [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is integrated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup. This topic provides instructions on how to install and configure [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and also includes a community-written link to upgrade the ESB Toolkit.  
  
> [!IMPORTANT]
>  You must have BizTalk Server installed before you start installing the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
## Installing [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]  
  
1.  On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation **Start** screen, click **Install [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**.  
  
2.  In **License Agreement**, accept the license agreement, and then select **Next**.  
  
3.  In **Component Installation**, select the components you want to install, and then select **Next**.  
  
4.  Review your component selection on the **Summary** screen, and then select **Install**.  
  
5.  Select **Finish** to close the installation wizard.  
  
## Configuring [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]  
  
> [!IMPORTANT]
>  You must configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] before configuring [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
1.  From the **Start** menu, expand **All Programs**, [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and then click **ESB Configuration Tool**.  
  
    > [!NOTE]
    >  You must run the ESB Configuration Tool as an administrator.  
  
2.  In the **ESB Configuration Tool**, from the left pane, select **ESB Configuration**. On the right pane, for **Database Server**, specify the database server name where the databases required for [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] are created.  
  
3.  In the **IIS Web Services** box, specify the user credentials under which the applications required for [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] are created. Also specify the name of the website in IIS under which the applications are created.  
  
4.  The **BizTalk User Groups** box lists the default user groups available for ESB configuration.  
  
    > [!IMPORTANT]
    >  At this stage, you can click **Apply Configuration** towards the top of the ESB Configuration Tool to configure the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] with the default settings. However, if you want to do a custom configuration, you can perform the remaining steps as well. In such a case, the values you specify in the subsequent steps take precedence over the default values.  
  
5.  From the left pane, expand **Exception Management**, and do the following:  
  
    -   Click the **Database** node, and clear the **Enable Exception Management Database** check box if you do not want to configure an exception management database.  
  
    -   Similarly, on the **Database** node, select the **Use Existing Database** checkbox if you want to use an existing database instead of the configuration tool creating a new database. You can also specify the database server name and the database name.  
  
    -   On the **Exception Web Services** node, clear the **Enable Exception Services** check box if you do not want to configure these services. Alternatively, if you want to run these services under a different website, you can specify that here too.  
  
6.  From the left pane, expand **ESB Core Components**, and do the following:  
  
    -   Click the **Itinerary Database** node, and clear the **Itinerary Database** check box if you do not want to configure an itinerary database.  
  
    -   Similarly, on the **Itinerary Database** node, select the **Use Existing Database** checkbox if you want to use an existing database instead of the configuration tool creating a new database. You can also specify the database server name and the database name.  
  
    -   On the **Core Web Services** node, clear the **Enable Core Services** check box if you do not want to configure these services. Alternatively, if you want to run these services under a different website, you can specify that here too.  
  
7.  From the left pane, click **Configuration** to specify the SSO configuration. If you are installing and configuring the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] in a single server environment, you should select **File Configuration Source**, which is the default selection. However, if you are setting up a multiple-machine deployment, you must select the **SSO Configuration Source**, and then provide the following values.  
  
    -   **SSO Server**: Name of the SSO server.  
  
    -   **Configuration file**: Click the ellipsis button **(…)**, and then browse to the Esb.config file, which is included in the ​Microsoft BizTalk ESB Toolkit  
  
    -   **Application Name**: Type a name for the SSO application. For example, `ESB Toolkit`.  
  
    -   **Contact Information**: Type the appropriate contact information in the following format: `someone@example.com`.  
  
    -   **Administrator Group Name**: Click the ellipsis button **(…)**, and then browse to the appropriate name  
  
    -   **User Group Name**: Click the ellipsis button **(…)**, and then browse to the appropriate name  
  
8.  Click **Apply Configuration**. Open IIS and notice that the applications required for [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] are now created under the website you specified while configuring [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
9. In the **ESB Configuration Tool**, on the **ESB BizTalk Applications** node, from the right pane, do the following:  
  
    -   Select the **Enable ESB Core Components in BizTalk Server** check box to create the application in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. Select the **Use Default Binding** to bind this application to the default host. Select the **Do not use Default Binding** if you do not want to bind the application to the default host. In such a case, you must explicitly bind the application to a host, once the application is created.  
  
    -   Select the **Enable ESB JMS/WMQ Components in BizTalk Server** check box to create the application in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. Select the **Use Default Binding** to bind this application to the default host. Select the **Do not use Default Binding** if you do not want to bind the application to the default host. In such a case, you must explicitly bind the application to a host, once the application is created.  
  
    -   Click **Apply Configuration** to create the applications you selected. Verify that the applications are created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## Upgrade ESB Toolkit 2.1 to 2.2 – Community Addition  
 [In-place upgrade of ESB Toolkit 2.1 to 2.2](http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html) (http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html)