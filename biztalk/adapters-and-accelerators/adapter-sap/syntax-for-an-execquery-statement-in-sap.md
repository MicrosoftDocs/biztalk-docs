---
title: "Syntax for an EXECQUERY Statement in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99bd7fbb-64f2-4327-a8ae-ccb574e56150
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Syntax for an EXECQUERY Statement in SAP
You can use the SAP GUI to create queries by graphically selecting the tables you want to query, the columns and sort order you want included in the result set, etc. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] enables users to execute such queries from an ADO.NET application by providing an EXECQUERY operation that users can use to execute a query defined in the SAP system.  
  
 The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC Z_EXECUTE_SAP_QUERY to execute the pre-defined queries in the SAP system. The custom RFC in turn executes the RSAQ_REMOTE_QUERY_CALL, which is a standard RFC defined in the SAP system. Hence, before you can use the EXECQUERY operation, you must install the custom RFC in the SAP system you will be running your queries against. For instructions on how to install the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
 This topic provides information on the syntax of the EXECQUERY operation, and other useful information related to the EXECQUERY operation.  
  
## Syntax for an EXECQUERY Statement  
 The following section describes the grammar specifications for using the EXECQUERY operation against the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
```  
EXECQUERY <QueryName> @USERGROUP='usergroup' [, @WORKSPACE='X'] [, @VARIANT='variant']   
[, @P1='<value 1>’] [, @P2='<value 2>'] ... [, @Pn = '<value n>'] [, @P1!='<value 3>'] [, @P1 > '<value 4>'] [, @P1 <= '<value 2>']   
[, NOT @P1 = '<value 2>'] [, NOT @P1 != '<value 2>'] [, NOT @P1 > '<value 2>']   
[, @P1 BETWEEN '<value 1>' AND '<value 2>'] [, NOT @P1 BETWEEN '<value 1>' AND '<value2>’]  
[OPTION 'USEORIGINALCOLUMNNAMES']  
  
```  
  
 where:  
  
- **\<QueryName\>** is the name of the query defined in the SAP system.  
  
- **USERGROUP** refers to the user group in which the query is defined. This is a mandatory parameter.  
  
- **WORKSPACE** refers to the workspace in which the query is defined. In SAP, there are two workspaces—Standard and Global. Provide an empty space to specify the Standard workspace. Provide `X` to specify the Global workspace. Default is empty space.  
  
- **VARIANT** refers to a saved set of selection criteria that you can specify while executing an SAP query. For example, you can use variants to specify default values for queries.  
  
- <strong>@Pn</strong> refers to the n<sup>th</sup> selection field in the SAP query definition.  
  
- **USEORIGINALCOLUMNNAMES** specifies whether the provider uses the original column names in the DataSet, as they exist in the SAP system. By default, the provider uses the friendly names defined in the SAP query. However, if the friendly names within the query are not unique, the ADO.NET client will throw an error while reading the data from the DataSet. In such scenarios, you must specify the USEORIGINALCOLUMNNAMES option, indicating that the provider uses the original column names in the DataSet.  
  
  > [!IMPORTANT]
  >  You must always provide the value for the OPTION keyword within single quotes, for example, '*USEORIGINALCOLUMNNAMES*'.  
  
> [!NOTE]
>  For information about how the parameters of an SAP Query translate into an EXECQUERY syntax, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).  
  
### Framing an EXECQUERY Syntax  
 Framing syntax for an EXECQUERY operation to execute an SAP query depends on how the query is defined in the SAP system, including each parameter value defined in SAP. For information about how to frame EXECQUERY syntax to execute an SAP query, see [Translate SAP query parameters into EXECQUERY command](../../adapters-and-accelerators/adapter-sap/translate-sap-query-parameters-into-execquery-command.md).  
  
### Additional Considerations While Using the EXECQUERY operation  
 This section lists the points that you must keep in mind when using the EXECQUERY statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
- The values specified for USERGROUP, WORKSPACE, and VARIANT are passed on as-is to the standard SAP RFC, RSAQ_REMOTE_QUERY_CALL. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not validate the values specified for these parameters.  
  
- All values returned by the EXECQUERY operation are of string type.  
  
- Keywords for query names, user group, workspace, and variants are not case sensitive. However, the parameter names must always be in upper caseP such as @P1, @P2, etc. For example:  
  
  ```  
  EXECQUERY xyz USERGROUP=’mygrp’, NOT @P1= 'somevalue'  
  ```  
  
   is the same as  
  
  ```  
  EXECQUERY xyz uSERgROUP=’mygrp’, NOT @P1= 'somevalue'  
  ```  
  
- The operators supported by the EXECQUERY are >, <, >=, <=, !=, NOT, and BETWEEN.  
  
- Wildcard characters are not supported by the EXECQUERY operation. For example, the following statement gives the expected output:  
  
  ```  
  EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
  ```  
  
   However, the same query when executed with a wildcard character gives an error. Notice the use of wildcard characters for <strong>@P2</strong>.  
  
  ```  
  EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024',  @P1 = '0000003262',@P2 = '*&*'  
  ```  
  
   In this example, you might get an error stating that no data was found. This is because the query searches for **'\*&\*'** as a string and does not consider asterisk (*) as a wildcard character.  
  
- You must always specify a date values in YYYYMMDD format.  
  
- If you are executing a query that has a variant defined in the SAP system, you can specify the name of the variant as part of the command. For example:  
  
  ```  
  EXECQUERY myquery @usergroup='mygroup',@variant = 'variant1'  
  ```  
  
  > [!NOTE]
  >  You do not need to specify a variant name if a default variant is defined for the query in the SAP system.  
  
## See Also  
 [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)