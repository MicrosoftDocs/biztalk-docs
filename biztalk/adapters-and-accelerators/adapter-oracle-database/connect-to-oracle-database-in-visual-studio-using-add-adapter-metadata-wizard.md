---
title: "Connect to Oracle Database in Visual Studio using Add Adapter Metadata Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 726b3f82-887c-407a-bb9f-dcb9443155b0
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to Oracle Database in Visual Studio using Add Adapter Metadata Wizard
The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is also exposed as a BizTalk adapter and, therefore, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on the Oracle database using the adapter.  

 This topic provides instructions on how to use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

## Connecting to an Oracle Database Using the Add Adapter Metadata Wizard  
 Perform the following steps to connect to an Oracle database using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To connect to an Oracle database  

1. To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:  

   1. Right-click the project in Solution Explorer, point to **Add**, and then click **Add Generated Items**.  

   2. In the **Add Generated Items** dialog box, do the following:  


      |    Use this    |           To do this            |
      |----------------|---------------------------------|
      | **Categories** |     Click **Add Adapter**.      |
      | **Templates**  | Click **Add Adapter Metadata**. |


   3. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

   4. In the Add Adapter Metadata Wizard, select **WCF-OracleDB**. Select the computer on which BizTalk Server is installed and the name of the BizTalk database.  

      > [!IMPORTANT]
      >  If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.  

   5. Click **Next**.  

2. From the **Select a binding** drop-down list, select **oracleDBBinding** and click **Configure**.  

3. In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** drop-down list box, select **Username** and specify the user name and password to connect to the Oracle database.  

   1. To connect using the Oracle database credentials, type the database credentials in the **User name** and **Password** text boxes. Make sure you adhere to the following considerations when specifying the user name and password to connect to an Oracle database:  

      - **User name**. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Oracle database. User names on the Oracle database are case-sensitive. You should ensure that you provide Oracle user names to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the case expected by your Oracle database. Typically, this means that the user name in the SCOTT/TIGER credential should be upper case: "SCOTT".  

      - **Password**. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Oracle database. For release 10g and earlier, passwords on the Oracle system are not case-sensitive.  

   2. To connect using Windows Authentication, type **/** in the **User name** text box and leave the **Password** text box blank.  

4. Click the **URI Properties** tab, and specify values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  

5. Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target. For example, if you want to target the POLLINGSTMT operation, you must set the **PollingStatement** binding property. For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).

   > [!NOTE]
   >  If you are generating metadata using Add Adapter Metadata Wizard and you selected an existing WCF-OracleDB send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  

6. Click **OK**.  

7. Click **Connect**. After the connection is established, the connection status is shown as **Connected**.  

    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established.  

    ![Consume Adapter Service dialog box connected](../../adapters-and-accelerators/adapter-oracle-database/media/b5bdb08c-4326-408b-8c2a-aedae64925c8.gif "b5bdb08c-4326-408b-8c2a-aedae64925c8")  

## See Also  
 [Connect to the Oracle Database in Visual Studio using the Add Adapter Service Reference](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-db-in-visual-studio-using-the-add-adapter-service.md)   
 [Connect to the Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)