---
title: "Configure a port using the WCF-SQL adapter in BizTalk | Microsoft Docs"
description: Create WCF-SQL send and receive ports to use the SQL Server adapter in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8cdc032-3160-43de-9510-7ca69506083e
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-SQL adapter
This topic provides instructions on how to configure WCF-SQL send and receive ports to perform outbound and inbound operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## Deploy adapters to send messages to SQL Server  
 Perform the following steps to configure a WCF-SQL send port for sending messages to SQL Server using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
4. Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
5. Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and SQL Server.  
  
6. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
7. From the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.  
  
8. In the transport properties dialog box, do the following:  
  
   1. Click the **General** tab, click the **Configure** button, and provide values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) for a list of actions for each operation. For example, the action to invoke the Insert operation on a table in a SQL Server database is:  
  
      ```  
      TableOp/Insert/dbo/Employee  
      ```  
  
      > [!NOTE]
      >  Employee is the name of a table in SQL Server database.  
  
   3. Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
      > [!NOTE]
      >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.  
  
   4. Click the **Credentials** tab, and then do one of the following:  
  
      -   Select the **Do not use Single Sign-On** option, and the specify the user name and password to connect to SQL Server. Note that the user name and password are case-sensitive.  
  
          > [!NOTE]
          >  If you want to connect to SQL Server using Windows authentication, specify a blank user name and password. Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
      -   Select the **Use Single Sign-On** option, and then specify an affiliate Enterprise Single Sign-on (SSO) application.  
  
           For more information about security with respect to BizTalk Server, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).  
  
   5. To return to the **Send Port Properties** dialog box, click **OK**.  
  
9. From the **Send handler** list, select **BizTalkServerApplication**.  
  
10. If you chose to create **Static One-Way Send Port** in step 5, specify a send pipeline. From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.  
  
11. If you chose to create **Static Solicit-Response Port** in step 5, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
12. Click **OK**.  
  
## Deploy adapters to receive messages from SQL Server  
 Perform the following steps to configure a WCF-SQL receive port for receiving messages from SQL Server using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
4. Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
5. Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and SQL Server.  
  
6. In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.  
  
7. On the **Receive Locations** tab, click **New**. The **Receive Location Properties** dialog box appears.  
  
8. In the **Receive Location Properties** dialog box, do the following:  
  
   1.  Specify a name for the receive location.  
  
   2.  From the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.  
  
9. In the transport properties dialog box, do the following:  
  
   1. Click the **General** tab, click the **Configure** button, and provide values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
   2. Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. For more information about binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
      > [!NOTE]
      >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.  
  
   3. Click the **Behavior** tab to set the transaction isolation level. For more information about setting transaction isolation level, see [Configure Transaction Isolation Level and Transaction Timeout with SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).  
  
   4. Click the **Other** tab, and do one of the following:  
  
      - Select **User account**, and specify the user name and password to connect to SQL Server. Note that the user name and password are case-sensitive.  
  
        > [!NOTE]
        >  If you want to connect to SQL Server using Windows authentication, specify a blank user name and password. Before you do this, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
      - Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  
  
         For more information about security with respect to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md).  
  
   5. To return to the **Receive Location Properties** dialog box, click **OK**.  
  
10. From the **Receive handler** drop-down list, select **BizTalkServerApplication**.  
  
11. If you chose to create **One-way Receive Port** in step 5, specify a receive pipeline. From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.  
  
12. If you chose to create **Request Response Receive Port** in step 5, specify send and receive pipelines.  
  
    1.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
    2.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
13. In the **Receive Location Properties** dialog box, click **OK**.  
  
14. In the **Receive Port Properties** dialog box, click **OK**.  
  
## See Also  
[Manually configure a physical port binding to the SQL adapter
](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)