---
title: "Step 5 (On Premises): Generate the Schema for Inserting a Message inito SalesOrder Table | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab0bc1a7-8bcd-4110-88e6-4eddf0b57068
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5 (On Premises): Generate the Schema for Inserting a Message inito SalesOrder Table
According to the business scenario, the X12 sales order message sent from Contoso must be inserted into Northwind’s **SalesOrder** table if the quantity ordered is greater than 100. To insert a message into a **SalesOrder** table, you must generate the schema for the **Insert** operation on the table. In this topic, you will create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution, and then use the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] to generate the schema for performing an **Insert** operation on the **SalesOrder** table.  

### To generate the schema for Insert operation on SalesOrder table  

1. Create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Visual Studio project. From the Visual Studio **File** menu, click **New**, and then click **Project**. In the **New Project** dialog box, from the list of installed templates, click **BizTalk Projects**, and then select **Empty [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Project**. For the project name enter `OrderProcessingDemo` and then click **OK**.  

2. Right-click the project name in Solution Explorer, point to **Add**, and then click **Add Generated Items**.  

3. In the **Add Generated Items** dialog box, select **Consume Adapter Service**, and then click **Add**. The [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] opens.  

4. From the **Select a binding** drop-down list, select **sqlBinding**, and then click **Configure**.  

5. In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential  type** drop-down list, do one of the following:  


   |  Click this  |                                                                                                                                                               To do this                                                                                                                                                               |
   |--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   **None**   |                                                                                                                                          Connect to SQL Server using Windows authentication.                                                                                                                                           |
   | **Windows**  |                                                                                                                                          Connect to SQL Server using Windows authentication.                                                                                                                                           |
   | **Username** | Specify the user name and password to connect to SQL Server by specifying credentials for a user defined in SQL Server database. Note that the user name and password are case-sensitive. **Note:**  If you leave the **User name** and **Password** fields as blank, the adapter connects to SQL Server using Windows authentication. |


6. Click the **URI Properties** tab, and then specify values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], see [SQL Server Connection URI](http://msdn.microsoft.com/library/dd788089.aspx).  

   > [!NOTE]
   >  If the connection parameters contain any reserved characters, you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. However, if you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  
   > 
   > [!NOTE]
   >  If you do not specify any values in the URI property tab, the [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] puts the URI as `mssql://.//`. In such a case, the adapter connects to the default database and the default database instance on the local computer.  

7. In the **Configure Adapter** dialog box, click **OK**. In the **Consume Adapter Service** dialog box, click **Connect**.  

8. From the **Select a category** box, expand **Tables**, and then click the **SalesOrder** table.  

9. From the **Available categories and operations** box, select **Insert**, click **Add**, and then click **OK**. New items are added to the Solution Explorer. The schema file (**TableOperation.dbo.SalesOrder.xsd**) is the generated schema for performing an Insert operation on the **SalesOrder** table.  

## See Also  
 [Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)