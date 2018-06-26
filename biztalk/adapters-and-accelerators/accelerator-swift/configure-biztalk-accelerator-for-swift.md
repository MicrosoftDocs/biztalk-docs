---
title: "Configure BizTalk Accelerator for SWIFT | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e34b0b2d-f563-468b-b6b9-536f0df96f52
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure BizTalk Accelerator for SWIFT

Configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]. 

When you install [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], there is a checkbox that lets you run the configuration automatically. Or, you can open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration listed in your apps.

This topic shows you how to configure the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] accelerator, how to export or import a configuration, and also lists the post-configuration steps.

## Configure A4SWIFT

1. Open the BizTalk Accelerator for SWIFT (A4SWIFT) Configuration.
2. Select **MCRR**. MCRR is available only if you installed the **Message Repair and New Submission** components.
3. When asked **Do you want to create a new database group**:

   * Select this option to create the new groups shown in the **Group** pane. 
   * To join an existing database group, uncheck this option.

4. If you installed **Web Components for Message Repair and New Submission**, then select **WebService**.
5. Select the web site to host the A4SWIFT Web service. By default, the Default Web Site is selected.
6. Select **Apply Configuration**.
7. In **Summary**, verify the configuration settings, and then click **Configure**. 

    > [!TIP] 
    > You can save the configuration settings as an XML file, if desired.

8. Select **Finish** when the configuration completes.

## Export or import a configuration
You can export the configuration settings of A4SWIFT to an XML file. These settings can then be imported to configure another A4SWIFT installation. 

### Export the configuration

1. Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Export Configuration**.
2. In **Save As**, browse to the folder where you want to save the configuration file, enter a name for the configuration file, and then **Save**.
3. When exported successfully, select **OK**.

### Import a configuration
1. Open the Microsoft BizTalk Accelerator for SWIFT Configuration, and select **Import Configuration**.
2. Browse to the folder that contains the configuration file, select the file, and then select **Import**.

## Post-configuration steps

### Add users to the A4SWIFT Users group

After you configure the [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)], add the account that runs the BizTalkServerApplication host instance to the **A4SWIFT Users** group (*not* the **A4SWIFT Administrators** group). 

**Steps**:

1. Open **Services**. Services is also available in **Server Manager**, and then **Tools**. 
2. In the list, find **BizTalk Service BizTalk Group: BizTalkServerApplication**. 
3. Double-select to open its properties.
4. In the **Log On** tab, note the user account listed as **This account**.
5. Open **Local Users and Groups** (in Computer Management), and then find the **A4SWIFT Users** group. Add the user account to this group.

> [!TIP] 
> The host instance account needs this group membership for the host Message Repair runtime component to access the BizTalk Server database.

### Check the identity of the application pool
The A4SWIFT_MRSR web service is hosted in an application in IIS. The application pool identity *cannot* be Network Service. Change the identity of the application pool to a local or domain account that is a member of the **A4SWIFT Users** group.

**Steps**:

1. Open **Internet Information Services Manager**. The IIS Manager is also available in **Server Manager**, and then **Tools**. 
2. Expand the **Default Web Site**, and select the A4SWIFT_MRSR web service. 
3. Select **Basic Settings**. The name of the application pool is listed.
4. In the left pane, select **Application Pools**, and then select your application pool.
5. Select **Advanced Settings**, and change the **Identity** if needed.