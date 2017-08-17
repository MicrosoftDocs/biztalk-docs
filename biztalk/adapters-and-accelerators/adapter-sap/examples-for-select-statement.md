---
title: "Examples for SELECT Statement in mySAP adapter in BizTalk| Microsoft Docs"
description: SELECT examples and samples using the mySAP adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54a5a4ac-a994-4706-9735-a5a1a82b893b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Examples for SELECT Statement
This topic shows example syntax for various SELECT statements.

## Sample statements 
  
-   To list details about flights listed in the table named SPFLI, use the following syntax:  
  
    ```  
    Select * from SPFLI  
    ```  
  
-   To store extracted data into a file named flight.txt at \\\SAPServer\Extracts, use the following syntax:  
  
    ```  
    Select * Into file '\\SAPServer\Extracts\flight.txt' from SPFLI  
    ```  
  
-   To list details of all flights from New York to San Francisco, use the following syntax:  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto='SAN FRANCISCO'  
    ```  
  
-   To list details of all flights from New York whose `connid` field values are between 1000 and 5000, use the following syntax:  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and (connid>1000 and connid<5000)  
    ```  
  
-   To list details of all flights from New York to a user-specified city, use the following syntax:  
  
    ```  
    Select * from SPFLI where cityfrom='NEW YORK' and cityto=@variable  
    ```  
  
     In this instance, create an SAP parameter named `@variable`, specify the value, and add it to the corresponding command object.  
  
-   In the LIKE clause of a SELECT query, only the percent sign, "%" (for any string of zero or more characters), and underscore, "_" (for any single character), are allowable special characters. All others are considered string values and are ignored.  
  
    -   Example to demonstrate the use of percentage "%"  
  
        ```  
        SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
        ```  
  
         Here, %MODE% fetches all records where Name1 contains the string "MODE".  
  
    -   Example to demonstrate the use of underscore "_"  
  
        ```  
        SELECT NAME1  AS [MYANME],  LAND1, KUNNR  from KNA1 where (NAME1 LIKE 'D_' )  
        ```  
  
         Here, "D_" fetches all records where Name1 starts with "D" and contains two characters.  
  
-   Example to demonstrate a "between" predicate clause  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT between 596 AND 999) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   Example to demonstrate a "not between" predicate clause  
  
    ```  
    SELECT NAME1, PSTLZ  from KNA1 where (MANDT not between 596 AND 599) AND NAME1 LIKE '%MODE%'  
    ```  
  
-   Example for SELECT statement using Join and a TOP clause  
  
    ```  
    SELECT TOP 1 * FROM spfli INNER JOIN sflight ON spfli.mandt = sflight.mandt  
    ```  
  
-   Example for SELECT statement using the OPTION clause  
  
    ```  
    SELECT top 50000 * from bseg option 'batchsize 20000'  
    ```  
