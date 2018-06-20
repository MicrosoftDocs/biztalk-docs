---
title: "Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, creating LOB schemas"
ms.assetid: 70e26dc9-4299-4d30-8f8b-5cc3469a2025
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor
In this step, you generate the schema to use to query the Contoso ERP system for the price and availability of a particular product. You generate this schema by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® SQL Adapter for BizTalk Server.  

### To update the SQL stored procedure for schema generation  

1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  

2.  In the Microsoft SQL Server Management Studio, expand **Databases**, expand **Contoso**, expand **Programmability**, and then expand **Stored Procedures**.  

3.  Right-click **dbo.SP_GetInventoryForProductID**, and then click **Modify**.  

4.  In the query window, insert a comma, a space, and then "xmldata" immediately following "for xml auto". The line of code should be the following:  

    ```  
    for xml auto, xmldata  
    ```  

5.  Click **Execute** to save the changes to the stored procedure.  

    > [!NOTE]
    >  Leave the Microsoft SQL Server Management Studio open for the next procedure.  

### To create the Contoso Price and Availability schema  

1. Open the Contoso solution in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

2. In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, point to **Add**, and then click **Add Generated Items**.  

3. In the Add Generated Iems dialog box, with **Add Adapter Metadata** selected in the left pane, click **Add Adapter Metadata** in the right pane, and then click **Add**.  

4. On the **Add Adapter Wizard** page, select **SQL** from the list of registered adapters, and then click **Next**.  

5. On the **Database Information** page, click **Set**.  

6. In the Data Link Properties dialog box, in the **Select or enter a server name** box, type **localhost**. Select **Use Windows NT Integrated security**. For **Select the database on the server**, select the **Contoso** database from the database list. Click **OK**.  

7. On the **Database Information** page, click **Next**.  

8. On the **Schema Information** page, do the following:  


   |                Use this                 |              To do this              |
   |-----------------------------------------|--------------------------------------|
   |          **Target namespace**           | Type **<http://Contoso.com/Price>**. |
   |        **Select the port type**         |        Select **Send port**.         |
   | **Request document root element name**  |      Type **rootPriceRequest**.      |
   | **Response document root element name** |     Type **rootPriceResponse**.      |


9. Click **Next**.  

10. On the **Statement type information** page, select **Stored Procedure**, and then click **Next**.  

11. On the **Statement Information** page, for **\<Select a stored procedure\>**, select **SP_GetInventoryForProductID** from the drop-down list. Click **Generate**, and then click **Next**.  

12. On the **Completing the SQL Transport Schema Generation Wizard** page, click **Finish** to import the schema into the ContosoPriceAndAvailability BizTalk project.  

13. In Solution Explorer, right-click the generated schema (SQLService_Price.xsd), click **Rename**, and type **ContosoPriceAndAvailability.xsd** as the new name for the schema. Click **Enter**.  

14. In the Properties window for the ContosoPriceAndAvailability schema, set the **Type Name** property to **ContosoPriceSchema**.  

15. By default, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a BizTalk orchestration named **BizTalk Orchestration.odx**. Right-click this orchestration, and then click **Delete** because you do not need this orchestration. In the popup indicating that the orchestration will be deleted permanently, click **OK**.  

16. In the Microsoft SQL Server Management Studio, remove the `xmldata` predicate and the comma from the `SP_GetInventoryForProductID` stored procedure that you added in the previous step, and then click **Execute**.  

## See Also  
 [Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)