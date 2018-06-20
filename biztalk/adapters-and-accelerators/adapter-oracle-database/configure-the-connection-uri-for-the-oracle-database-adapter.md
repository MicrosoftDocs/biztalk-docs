---
title: "Configure the connection URI for the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection URI, specifying at design time"
  - "connection URI, specifying at run time"
ms.assetid: 9f302b67-0bcc-44d1-9517-10d402873540
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the connection URI for the Oracle Database adapter
A connection URI is a connection string that contains parameters required to connect to the Oracle database. While using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the URI to connect to the Oracle database to generate the metadata. While configuring an orchestration using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the URI to connect to the Oracle database to perform operations.  

## Specifying the Connection URI from Visual Studio  
 From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To specify the Connection URI using Consume Adapter Service Add-in  

1. Right-click your BizTalk project, and then select **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |             To do this             |
   |----------------|------------------------------------|
   | **Categories** | Click **Consume Adapter Service**. |
   | **Templates**  | Click **Consume Adapter Service**. |


3. To start the **Consume Adapter Service** dialog box, click **Add**.  

4. In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and click **Configure**.  

5. In the **Configure Adapter** dialog box, click the **Security** tab and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database:  

   -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  

   -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  

6. Click the **URI Properties** tab, and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  

7. Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema. For more information about binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  

8. Click **OK**.  

#### To specify the Connection URI using Add Adapter Metadata Wizard  

1. Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |           To do this            |
   |----------------|---------------------------------|
   | **Categories** |     Click **Add Adapter**.      |
   | **Templates**  | Click **Add Adapter Metadata**. |


3. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

4. In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleDB**. Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.  

   > [!IMPORTANT]
   >  If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.  

5. Click **Next**.  

6. In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleDBBinding**, and then click **Configure**.  

7. In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle database:  

   -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  

   -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  

8. Click the **URI Properties** tab, and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  

9. Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema. For more information about binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  

10. Click **OK**.  

## Specifying the Connection URI from the BizTalk Server Administration Console  
 From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the credentials as part of the WCF-Custom or WCF-OracleDB port configuration.  

#### To specify the Connection URI for the WCF-Custom Port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  

4. For a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an Oracle database.  

       -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  

       -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  

   -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

5. For a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab and do one of the following:  

   -   Select **User account** option, and specify the user name and password to connect to an Oracle database.  

       -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  

       -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  

   -   Select **Get credentials from affiliate application** option, and specify an affiliate application.  

6. Click **OK**.  

#### To specify the Connection URI for the WCF-OracleDB port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. Add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  

3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

4. In the port properties dialog box, from the **Type** drop-down list, select **WCF-OracleDB**, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

5. In the port properties dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleDBBinding**.  

6. If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to the Oracle database.  

       -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  

       -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  

   -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

7. If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:  

   -   Select **User account** option, and specify the user name and password to connect to the Oracle database.  

       -   To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes.  

       -   To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  

   -   Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  

8. Click **OK**.  

## See Also  
[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)   
 [Connect to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)