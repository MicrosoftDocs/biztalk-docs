---
title: "Connect to SQL Server in Visual Studio Using Add Adapter Metadata Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2169722d-beba-4d96-a54b-54986ece9bf8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to SQL Server in Visual Studio Using Add Adapter Metadata Wizard
The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is also exposed as a BizTalk adapter and, therefore, you can use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for the operations you want to perform on SQL Server using the adapter.  

## Connecting to SQL Server Using Add Adapter Metadata Wizard  
 Perform the following steps to connect to SQL Server using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To connect to SQL Server  

1. To connect using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in a BizTalk solution:  

   1. Create a BizTalk project using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

   2. Right-click the project name in Solution Explorer, point to **Add**, and then click **Add Generated Items**.  

   3. In the **Add Generated Items** dialog box, do the following:  


      |    Use this    |           To do this            |
      |----------------|---------------------------------|
      | **Categories** |     Click **Add Adapter**.      |
      | **Templates**  | Click **Add Adapter Metadata**. |


   4. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

   5. In the Add Adapter Wizard, select **WCF-SQL**. Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.  

      > [!IMPORTANT]
      >  If you already have a WCF-SQL port configured in BizTalk, select the port from the **Port** list.  

   6. Click **Next**.  

2. From the **Select a binding** drop-down list, select **sqlBinding**, and then click **Configure**.  

3. In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential  type** drop-down list, do one of the following:  

   > [!NOTE]
   >  If you are connecting to SQL Server using Windows Authentication, the Windows user with which you are logged in must be added to SQL Server as described in [Connect to SQL Server using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  

   |  Click this  |                                                                                                                                                               To do this                                                                                                                                                               |
   |--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   **None**   |                                                                                                                                         Connect to SQL Server by using Windows authentication.                                                                                                                                         |
   | **Windows**  |                                                                                                                                         Connect to SQL Server by using Windows authentication.                                                                                                                                         |
   | **Username** | Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database. Note that the user name and password are case-sensitive. **Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication. |


4. Click the **URI Properties** tab, and then specify values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  

   > [!NOTE]
   >  If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  
   > 
   > [!NOTE]
   >  If you do not specify any values in the URI property tab, the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] puts the URI as `mssql://.//`. In such a case, the adapter connects to the default database and the default database instance on the local computer.  

5. Click the **Binding Properties** tab, and then specify values for the binding properties, if any, required by the operations you want to target. For more information about binding properties see, [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  

   > [!NOTE]
   >  If you are generating metadata using [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] and you selected an existing WCF-SQL send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  

6. Click **OK**.  

7. Click **Connect**. After the connection is established, the connection status is shown as **Connected**.  

    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immediately after the connection is established. The graphical user interface is same for the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

    ![Connect to SQL Server](../../adapters-and-accelerators/adapter-sql/media/661adb8a-5050-44d5-8db8-fdf0fe530b40.gif "661adb8a-5050-44d5-8db8-fdf0fe530b40")  

    The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] displays different nodes containing various operations that can be performed on SQL Server. For example, the **Procedures** node contains all the procedures available for the database you connected to. Similarly, the **Tables** node contains all the tables in the database you connected to, and the operations that can be performed on a table. For more information about these nodes, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md).  

## See Also  
 [Connect to SQL Server in Visual Studio using the Consume Adapter Service Add-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)