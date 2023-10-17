---
title: "Examples for EXEC Statement in mySAP adapter in BizTalk | Microsoft Docs"
description: EXEC examples and samples using the mySAP adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad2691f4-34bb-423c-9b3e-4abe2d55ddac
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Examples for EXEC Statement
This topic shows example syntax for various EXEC statements.

## Sample statements 
  
-   To execute a BAPI that takes no input parameters, use the following syntax; data is returned through a **DataReader** object:  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST  
    ```  
  
-   To execute an RFC that takes input parameters, use the following syntax:  
  
    ```  
    EXEC RFC_CUSTOMER_GET @NAME1='Contoso'  
    ```  
  
-   To execute an RFC that takes input parameters specified as a variable, use the following syntax:  
  
    ```  
    EXEC RFC_CUSTOMER_GET @var=@var  
    ```  
  
     In this example, you must create a parameter named `@var` and set the value explicitly (for example, to 1001), because the first parameter for RFC_CUSTOMER_GET corresponds to KUNNR (Customer Number)  
  
-   To execute an RFC that uses a variable for the input parameter name, use the following syntax:  
  
    ```  
    EXEC RFC_CUSTOMER_GET @KUNNR=@var1, @NAME1='Contoso'  
    ```  
  
     You must create a parameter named `@var1`, specify the value, and then bind it to the corresponding command object. The default direction of the newly created parameter object is `input`.  
  
-   To execute a BAPI and return tables as a parameter, use the following syntax:  
  
    ```  
    EXEC BAPI_COMPANYCODE_GETLIST @COMPANYCODE_LIST=@var1 OUTPUT  
    ```  
  
     You must create a parameter named `@var1`, specify the value, and bind it to the corresponding command object. The direction of the newly created parameter object should be `InputOutput` or `Output`.  
  
-   The following EXEC example uses a table complex type parameter. In the example, @fields is a TABLE parameter.  
  
    ```  
    exec rfc_read_table @query_table='BNKA', @fields='<FIELDS xmlns='http://Microsoft.LobServices.Sap/2007/03/Rfc/'>  
                <RFC_DB_FLD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                  <FIELDNAME>BANKL</FIELDNAME>  
                </RFC_DB_FLD>  
                <RFC_DB_FLD  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                    <FIELDNAME>BANKS</FIELDNAME>  
                </RFC_DB_FLD>  
              </FIELDS>', @fields=@flds output  
    ```  
  
-   The following EXEC example uses a STRUCT complex type. In the example, @equimaster is a STRUCT parameter.  
  
    ```  
    exec BAPI_EQMT_MODIFY @equipment='000000000000000637', @equimaster='<EQUIMASTER>           
                <EQUIPMENT xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">equip</EQUIPMENT>  
                <EQUICATGRY xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">E</EQUICATGRY>  
                <MATERIAL xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">mat</MATERIAL>  
              </EQUIMASTER >', @equimaster=@em output  
    ```  
  
## Support for Complex Parameter Types  
 There are two ways to support complex RFC parameters (tables and structures) when you use the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:  
  
- Provide an inline XML value for the complex type. This example shows how to pass XML to the complex parameter type *fields*. In the following example, <em>@fields</em> is a table parameter.  
  
  ```  
  exec rfc_read_table @query_table='BNKA', @fields='<FIELDS xmlns='http://Microsoft.LobServices.Sap/2007/03/Rfc/'>  
              <RFC_DB_FLD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                <FIELDNAME>BANKL</FIELDNAME>  
              </RFC_DB_FLD>  
              <RFC_DB_FLD  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
                  <FIELDNAME>BANKS</FIELDNAME>  
              </RFC_DB_FLD>  
            </FIELDS>', @fields=@flds output  
  ```  
  
- Create a **DataTable** parameter with columns for the fields in the complex type and set the SAP parameter value to **DataTable**. This example shows how to set the @fields complex type by using a **DataTable**.  
  
  ```  
  cmd.CommandText = "exec rfc_read_table @query_table='BNKA', @fields = @p_fields";  
  DataTable dt = new DataTable();  
  dt.Columns.Add("FIELDNAME");  
  SAPParameter p = new SAPParameter("@p_fields");  
  p.Value = dt;  
  ```  
  
## Limitations  
 The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] has the following limitations for complex types.  
  
- When you pass a complex type in a parameter by using a **DataTable**, you must include all fields (columns) of the complex type in the **DataTable**.  
  
- The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] does not support **DbNull**. You cannot set **DbNull** as a value for parameters.  
  
