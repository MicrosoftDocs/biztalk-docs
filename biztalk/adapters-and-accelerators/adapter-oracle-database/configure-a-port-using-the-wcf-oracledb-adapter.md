---
title: "Configure a port using the WCF-OracleDB adapter in BizTalk | Microsoft Docs"
description: Create WCF-OracleDB send and receive ports to use the Oracle DB adapter in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9eafefb-9b30-4801-9be9-6034ae0d3b7d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-OracleDB adapter
How to configure WCF-OracleDB send and receive ports to perform outbound and inbound operations on the Oracle database using the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx). 
  
## Deploy adapters to send messages to Oracle Database  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
4. Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
5. Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the Oracle database.  
  
6. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
7. From the **Type** drop-down list, select WCF-OracleDB, and then click **Configure**.  
  
8. In the transport properties dialog box, do the following:  
  
   1. Click the **General** tab, click the **Configure** button and provide values for the connection parameters. For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) for a list of actions for each operation. For example, the action to invoke the Insert operation an EMPLOYEE table under the HR schema in an Oracle database is:  
  
      ```  
      http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEE/Select  
      ```  
  
   3. Click the **Binding** tab and specify values for the binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).
  
      > [!NOTE]
      >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.  
  
   4. Click the **Credentials** tab, and then do one of the following:  
  
      -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.  
  
          -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  
  
          -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  
  
      -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  
  
   5. To return to the **Send Port Properties** dialog box, click **OK**.  
  
9. From the **Send handler** list, select **BizTalkServerApplication**.  
  
10. If you chose **Static One-Way Send Port** in step 5, specify a send pipeline. From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.  
  
11. If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
12. Click **OK**.  
  
## Deploy adapters to receive messages from Oracle Database  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
4. Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
5. Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the Oracle database.  
  
6. In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.  
  
7. On the **Receive Locations** tab, click **New**. The **Receive Location Properties** dialog box appears.  
  
8. In the **Receive Location Properties** dialog box, do the following:  
  
   1.  Specify a name for the receive location.  
  
   2.  From the **Type** drop-down list, select WCF-OracleDB, and then click **Configure**.  
  
9. In the transport properties dialog box, do the following:  
  
   1. Click the **General** tab, click the **Configure** button, and provide values for the connection parameters. For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
   2. Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).
  
      > [!NOTE]
      >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.  
  
   3. Click the **Behavior** tab to set the transaction isolation level. For more information about setting transaction isolation level, see [Configure transaction isolation level and transaction timeout](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md).  
  
   4. Click the **Others** tab, and do one of the following:  
  
      -   Select **User account** option, and specify the user name and password to connect to the Oracle database.  
  
          -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  
  
          -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  
  
      -   Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  
  
   5. To return to the **Receive Location Properties** dialog box, click **OK**.  
  
10. From the **Receive handler** drop-down list, select **BizTalkServerApplication**.  
  
11. If you chose **One-way Receive Port** in step 5, specify a receive pipeline. From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.  
  
12. If you chose **Request Response Receive Port** in step 5, specify send and receive pipelines.  
  
    1.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
    2.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
13. In the **Receive Location Properties** dialog box, click **OK**.  
  
14. In the **Receive Port Properties** dialog box, click **OK**.  
  
## See Also  
   [Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)
 
 [Connect to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)