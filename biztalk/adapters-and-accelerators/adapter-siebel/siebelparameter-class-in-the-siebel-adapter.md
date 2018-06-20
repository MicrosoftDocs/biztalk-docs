---
title: "SiebelParameter class in the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SiebelParameter"
  - "Data Provider for Siebel, SiebelParameter"
  - "SiebelParameter, supported properties and methods"
ms.assetid: 1dcb72c7-a470-4609-8aba-a5c8ad5f3ac9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SiebelParameter class in the Siebel adapter
The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbParameter` implementation to enable an ADO.NET client to specify parameters for a particular command. Using an instance of the `System.Data.Common.DbCommand` class of the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], a client program can obtain an instance of the `System.Data.Common.DbParameter` class.  

```  
//In this example, command is an instance of DbCommand  
DbParameter param = command.CreateParameter();  
```  

 Alternatively, the following approach can be used:  

```  

//Here command is an instance of SiebelCommand  
SiebelParameter param = (SiebelParameter) command.CreateParameter();                  
param.ParameterName = "@Time";  
```  

 The `SiebelParameter` class inherits from `DbParameter`.  It exists in the namespace `Microsoft.Data.SiebelClient`.  

## Supported Properties  
 The `SiebelParameter` class supports the following `DbParameter`*public* properties:  


|       Name        |   Get/Set   |                                                                                                            Description                                                                                                            |
|-------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    **DbType**     | Get and Set |                                               Data type of the parameter. See [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).                                               |
|   **Direction**   | Get and Set | The following values are supported:<br /><br /> -                     `ParameterDirection.Input`<br /><br /> -                     `ParameterDirection.Output`<br /><br /> -                     `ParameterDirection.InputOutput` |
|  **IsNullable**   | Get and Set |                                                                               The property is not supported, and will throw an exception if called.                                                                               |
| **ParameterName** | Get and Set |                                  The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports this property for an ADO.NET client to specify the parameter name.                                  |
|     **Value**     | Get and Set |                                                    The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] represents parameter values as strings.                                                    |

###  <a name="BKMK_Datatypes"></a> Supported Data Types  
 The following table summarizes the simple Siebel field types that [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports. For more detailed coverage, see [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).  

|Siebel Field Type|.NET Type|XML Schema Type|  
|-----------------------|---------------|---------------------|  
|DTYPE_BOOL|Boolean|xsd:boolean|  
|DTYPE_CURRENCY|Decimal|xsd:decimal|  
|DTYPE_DATE|DateTime|xsd:dateTime|  
|DTYPE_DATETIME|DateTime|xsd:dateTime|  
|DTYPE_ UTCDATETIME|DateTime|xsd:dateTime|  
|DTYPE_ID|String|xsd:string|  
|DTYPE_INTEGER|Integer|xsd:int|  
|DTYPE_NOTE|String|xsd:string|  
|DTYPE_NUMBER|Decimal|xsd:decimal|  
|DTYPE_PHONE|String|xsd:string|  
|DTYPE_TEXT|String|xsd:string|  
|DTYPE_TIME|DateTime|xsd:dateTime|  

## Supported Methods  
 The `SiebelParameter` class does not override any special methods in `DbParameter`.  

## See Also  
 [Extend ADO.NET Interfaces with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)