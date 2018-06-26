---
title: "Configure a port using the WCF-custom adapter and Oracle Database adapter | Microsoft Docs"
description: Create WCF-custom send and receive ports to use the Oracle DB adapter in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c99ff526-ad97-4095-812f-0ce88b071e7f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-custom adapter and Oracle Database adapter
How to configure WCF-Custom send and receive ports to perform outbound and inbound operations on the Oracle database using the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. See [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx) for permissions guidance.
  
## Deploy adapters for sending messages to an Oracle database  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
3. Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
4. Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the Oracle database.  
  
5. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
6. From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
7. In the **WCF-Custom Transport Properties** dialog box, do the following:  
  
   1. Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the Oracle database. For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md) for a list of actions for each operation. For example, the action to invoke the Insert operation an EMPLOYEE table under the HR schema in an Oracle database is:  
  
      ```  
      http://Microsoft.LobServices.OracleDB/2007/03/HR/Table/EMPLOYEE/Select  
      ```  
  
   3. Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleDBBinding**. You can specify the different binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
   4. Click the **Credentials** tab and do one of the following:  
  
      - Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.  
  
        -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  
  
        -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  
  
      - Select the **Use Single Sign-On** option, and specify an affiliate SSO application.  
  
        For more information about security with respect to BizTalk Server, see [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).  
  
        To return to the **Send Port Properties** dialog box, click **OK**.  
  
8. From the **Send handler** drop-down list, select **BizTalkServerApplication**.  
  
9. If you chose **Static One-Way Send Port** in step 4, specify a send pipeline. From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
10. If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
11. Click **OK**.  
  
## Deploy adapters for receiving messages from an Oracle database  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
3. Expand the application under which you want to deploy the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
4. Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between BizTalk Server and the Oracle database.  
  
5. In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.  
  
6. On the **Receive Locations** tab, click **New**. The **Receive Location Properties** dialog box appears.  
  
7. In the **Receive Location Properties** dialog box, do the following:  
  
   1.  Specify a name for the receive location.  
  
   2.  From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
8. In the **WCF-Custom Transport Properties** dialog box, do the following:  
  
   1. Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the Oracle database. For more information about the connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
   2. Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleDBBinding**. You can specify the different binding properties exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
   3. Click the **Others** tab, and do one of the following:  
  
      - Select **User account**, and specify the user name and password to connect to an Oracle database.  
  
        -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  
  
        -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  
  
      - Select **Get credentials from affiliate application** option, and specify an affiliate application.  
  
        For more information about security with respect to BizTalk Server, see [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md).
  
        To return to the **Receive Location Properties** dialog box, click **OK**.  
  
9. From the **Receive handler** drop-down list, select **BizTalkServerApplication**.  
  
10. If you chose **One-way Receive Port** in step 4, specify a receive pipeline. From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
11. If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.  
  
    1.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
    2.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
12. In the **Receive Location Properties** dialog box, click **OK**.  
  
13. In the **Receive Port Properties** dialog box, click **OK**.  
  
## See Also  
[Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)   
 [Connect to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)