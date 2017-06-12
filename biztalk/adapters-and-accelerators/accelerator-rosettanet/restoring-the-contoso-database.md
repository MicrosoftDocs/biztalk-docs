---
title: "Restoring the Contoso Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, restoring databases"
  - "databases, restoring"
ms.assetid: 291178c1-826e-49e0-a1d2-cbffee749659
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restoring the Contoso Database
In this step, you use SQL Server Management Studio to run a SQL script to restore the Contoso database and its associated stored procedures. You also populate the database tables with preliminary data.  
  
### To restore the Contoso database  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.  
  
2.  In the Connect to Server dialog box, in the **SQL Server** box, click **Connect**.  
  
    > [!NOTE]
    >  If the SQL Server Agent is not started, right-click it, and then click **Start**.  
  
3.  In the Microsoft SQL Server Management Studio, click **New Query**.  
  
4.  In the Query pane, copy and paste the following SQL script into the Query window:  
  
    ```  
    CREATE DATABASE Contoso  
    GO  
    USE Contoso  
    GO  
    CREATE TABLE Products (  
    [ProductID] [varchar] (255) NOT NULL ,  
    [Name] [varchar] (255) NOT NULL ,  
    [Description] [varchar] (800) NULL ,  
    [Price] [money] NULL ,  
    [NumberAvailable] [int] NOT NULL   
    ) ON [PRIMARY]  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901234', 'ADM Line Card','',200.65,820 )  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901235','Analog Line Card','',165.24,769 )  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901236', 'Mapper/MUX','',150.54,948)  
    GO  
    CREATE TABLE StatusCodes (  
    [statusID] [int] NOT NULL ,  
    [statusCode] [nvarchar] (50) NOT NULL   
    ) ON [PRIMARY]  
    GO  
    CREATE PROCEDURE GetInventoryForProductID  
    @ProductID varchar(255),  
    @NumberAvailable INT OUTPUT,  
    @Price MONEY OUTPUT  
    AS  
    SET NOCOUNT ON  
    SELECT @NumberAvailable = NumberAvailable,  
     @Price = Price  
    FROM Products  
    WHERE  ProductID = @ProductID  
    RETURN(0)  
    GO  
    CREATE PROCEDURE SP_GetInventoryForProductID  
    @ProductID varchar(255)  
    AS  
    SET NOCOUNT ON  
    SELECT *  
    FROM Products  
    WHERE ProductID = @ProductID  
    for xml auto  
    RETURN(0)  
    ```  
  
5.  Click **Execute**.  
  
### To set permissions on the Contoso database  
  
1.  In the Object Explorer of the Microsoft SQL Server Management Studio, expand **Databases**, expand the **Contoso** database, and then expand **Security**. Right-click **Users**, and then click **New User**.  
  
2.  In the Database User - New dialog box, for **Login name**, click the ellipsis.  
  
3.  In the Select Login dialog box, click **Browse**.  
  
4.  In the Browse for Objects dialog box, select **BizTalk Application Users**, and then click **OK**.  
  
5.  In the Select Login dialog box, click **OK**.  
  
6.  In the Database User - New dialog box, in the **Database role membership** pane, select **db_datareader** and **db_datawriter**. For **User name**, enter **BizTalk Application Users**. Click **OK**.  
  
7.  Repeat steps 1 through 6 for **BizTalk Isolated Host Users**, selecting **db_datareader** and **db_datawriter** for **Database role membership**, and entering **BizTalk Isolated Host Users** for **User name**.  
  
8.  Repeat steps 1 through 6 for **BizTalk Server Administrators**, selecting **db_owner** for **Database role membership**, and entering **BizTalk Server Administrators** for **User name**.  
  
## See Also  
 [Generating and Enabling Certificates](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)