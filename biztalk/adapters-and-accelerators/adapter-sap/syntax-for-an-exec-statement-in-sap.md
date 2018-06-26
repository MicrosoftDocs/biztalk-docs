---
title: "Syntax for an EXEC Statement in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "EXEC statement, syntax for"
ms.assetid: 406b1100-39a0-4321-89c9-ec1b8a3cfdc6
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Syntax for an EXEC Statement in SAP
The following section describes grammar specifications for implementing EXEC statements against the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]. Notice that in several cases, the syntax is somewhat different from Transact-SQL syntax.  
  
```  
EXEC rfc_name {<argument_element>} [ , …n ]  {;}[0,1] [ OPTION <disabledatavalidation>, <firstresultset> ]  
```  
  
 where:  
  
- **rfc_name** specifies the name of the function call to execute.  
  
- **<argument_element>** ::= @param_name = [0,1] \<const\> {[ INPUT &#124; OUTPUT ]}[0,1]  
  
  -   **param_name** specifies the parameter name defined in the function interface.  
  
  -   **\<const\>** ::= integer &#124; real &#124; string &#124; ? &#124; NULL &#124; xml_element  
  
- **OPTION**  provides option on how you want to present the data. The available options are:  
  
  - **disabledatavalidation** option sets the **EnableSafeTyping** binding property in the underlying [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. When safe typing is enabled the DATS, TIMS, and NUMC data types are represented as strings. For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
  - **firstresultset** specifies the first result set that is returned by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]. When any statement is executed on an ADO Provider source, only the first result set returned is available. For RFC EXEC scenarios, usually multiple table parameters are returned but if only the first result set is available for the client program, which might not be of use. By specifying the “firstresultset” keyword as part of the OPTION clause, clients can specify the first table parameter that they want the Provider to return. For example:  
  
    ```  
    EXEC Z_TEST_ALL_TYPES @P_IN='TestInput' OPTION 'disabledatavalidation', firstresultset TAB_ALLTYPES'  
    ```  
  
     In this example, the EXEC statement specifies that the first table parameter returned should be TAB_ALLTYPES.  
  
  > [!IMPORTANT]
  >  You must always provide the values for the OPTION keyword within single quotes, for example, '*disabledatavalidation*'.  
  
  In the preceding syntax, xml_element can be used to provide input for complex types. The xml element structure will be different for structures and tables. The xml_element for structure resembles the following:  
  
```  
<PARAM_NAME>  
    <FIELDNAME_1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_1>  
    <FIELDNAME_2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">value</FIELDNAME_2>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 The xml_element for table resembles the following:  
  
```  
<PARAM_NAME>  
    <STRUCT_NAME  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
        <FIELDNAME_1>value</FIELDNAME_1>  
    <STRUCT_NAME/>  
    <STRUCT_NAME  xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
        <FIELDNAME_1>value</FIELDNAME_1>  
    <STRUCT_NAME/>  
    ...  
    ...  
</ PARAM_NAME>  
```  
  
 For example, the XML element for a structure type resembles the following:  
  
```  
<INOUT_STRUCT>  
       <ACCPFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006</ACCPFIELD>  
       <CHARFIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">John</CHARFIELD>                 
</INOUT_STRUCT>  
```  
  
 Similarly, the XML element for a table type resembles the following:  
  
```  
<TAB_ALLTYPES>   
<ZZSTRUCTALLTYPES_RFC xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
       <ACCPFIELD>2006</ACCPFIELD>  
       <CHARFIELD>John</CHARFIELD>                          
</ZZSTRUCTALLTYPES_RFC>  
<ZZSTRUCTALLTYPES_RFC xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
       <ACCPFIELD>2007</ACCPFIELD>  
       <CHARFIELD>James</CHARFIELD>                          
</ZZSTRUCTALLTYPES_RFC>  
</TAB_ALLTYPES>  
```  
  
 For example statements, see [Examples for EXEC Statement](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).  
  
## Handling Named Parameters  
 The following are guidelines for specifying named parameters in EXEC queries:  
  
- You must specify parameters by naming them (for example, @param_name=value).  
  
  > [!NOTE]
  >  Unnamed parameters are not supported  
  
- When a parameter is defined using a default value, you can execute the procedure without specifying a parameter.  
  
- EXEC queries do not support using parameters with the following properties:  
  
  - Nested structures (structures that contain structures as their fields).  
  
  - Nested tables.  
  
  - A table containing a structure.  
  
  - A structure containing a table.  
  
  - A structure or table that has fields with composite string types, for example `SSTRING` or `RAWSTRING`.  
  
    The following table lists logical mappings between RFC parameter types and parameter directions when executing an RFC.  
  
  |RFC Param Type|Query Keyword|Parameter Direction|  
  |--------------------|-------------------|-------------------------|  
  |Import parameters|Nothing|Paramdirection.Input|  
  |Export parameters|Output|Paramdirection.Output|  
  |Table parameters|Output/Nothing|InputOutput|  
  
  The following are general guidelines for handling parameters:  
  
- You can specify parameter values either as constants or by using placeholders in the query.  
  
- When using placeholders in the query, you must create a `SAPParameter` object and add it to the corresponding command object. You then pass the placeholder name to the constructor; the direction and value depend on the context.  
  
  -   For `Input` parameters, do not specify in the query a keyword for the parameter direction. The `value` field of the parameter object must be set, or the provider will throw an exception. You must not explicitly set the `direction` field of the parameter object, because the provider defaults to `Input`.  
  
  -   For other parameters, use the form `@paramname=@placeholder` and specify the `Output` keyword explicitly in the query. You must then add a `SAPParameter` that corresponds with the placeholder and explicitly set the parameter direction to either `ParamDirection.Output` or `ParamDirection.InputOutput`, depending on the parameter type.  
  
- Parameter names and placeholder names are not case-sensitive.  
  
- Parameter names cannot be repeated in a query unless they have different directions.  
  
- Placeholder names cannot be repeated in a query.  
  
## Considerations When Calling an EXEC Statement  
 This section lists the points that you must keep in mind when using the EXEC statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
- For an EXEC statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.DateTime` objects.  
  
  > [!NOTE]
  >  For a SELECT statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `TIMS` field values as .NET `System.TimeSpan` objects. For more information about the SELECT statement, see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).  
  
## See Also  
 [About the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)