---
title: "Examples for EXECQUERY Statement in mySAP adapter in BizTalk | Microsoft Docs"
description: EXECQUERY examples and samples using the mySAP adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4139af16-7c38-4ea2-b3e5-5acf8fc1f3c4
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Examples for EXECQUERY Statement
This topic provides sample EXECQUERY statements.  


## Sample statements
-   Command to execute a query that takes two parameters P1 and P2.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
-   Command to execute a query that takes a range of value for parameter P1.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   Command to execute a query that takes values for parameter P1 outside a particular range.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   Command to execute a query that can take one of two values for parameter P1.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262', @P1 = '0000003263'  
    ```  
  
-   Command to execute a query that cannot take specific values for parameters.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 = '0000003262', NOT @P2 = '0000003263'  
    ```  
  
     In this example, P1 can have any value other than '0000003262'. Similarly, P2 can have any value other than '0000003263'.  
  
-   Command to execute a query that has variants defined in the SAP system.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant = ‘variant1’  
    ```  
  
     Variants refer to a saved set of selection criteria that you can specify while executing an SAP query. For example, you can use variants to specify default values for queries. For queries that have variants defined for all parameters, you do not need to specify the parameters in the command text.  
  
-   Command to execute a query that does not require a parameter.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'some_dummy_value'  
    ```  
  
     For queries that do not take parameter, you must specify a parameter with a dummy value.  
  
-   Command to execute a query containing a parameter expecting a date value.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '20080606'  
    ```  
  
     For queries that take parameters expecting date values, you must specify the date as YYYYMMDD.  
  
-   Command to execute a query by specifying null values for parameters.  
  
     For such queries, you cannot specify a query as:  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'null'  
    ```  
  
     Instead, if you do not want to specify a value, you should not specify P1 at all.  
  
-   Command to execute a query containing a parameter expecting a value greater than a certain number.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 > '0000003262'  
    ```  
  
-   Command to execute a query containing a parameter expecting a value lesser than a certain number.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 < '0000003262'  
    ```  
  
-   Command to execute a query containing a parameter expecting a value greater or equal to a certain number.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 >= '0000003262'  
    ```  
  
-   Command to execute a query containing a parameter expecting a value lesser or equal to a certain number.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 <= '0000003262'  
    ```  
  
-   Command to execute a query containing a parameter expecting a value not equal to a certain number.  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 != '0000003262'  
    ```  
  