---
title: "Value Mapping Functoid vs Value Mapping (Flattening) Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9f39814-8506-4319-860d-42c693206b34
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Value Mapping Functoid vs Value Mapping (Flattening) Functoid Reference
The **Value Mapping** and **Value Mapping (Flattening)** functoids transform data between different message formats. This is useful when transforming non-flattened messages into flattened messages or when using **Logical** functoids to split a source message into different elements in the target message.  
  
 This topic demonstrates how to map a non-flattened message into a flattened message by using three different schemas (listed below) that define messages containing information about products.  
  
-   Catalog  
  
-   FlattenedCatalog  
  
-   CategorizedCatalog  
  
## Using Value Mapping Functoid  
 In this scenario, FlattenedCatalog is the source schema and CategorizedCatalog is the destination schema. Now, map a flattened FlattenedCatalog message into a flattened CategorizedCatalog message using **Value Mapping** and **Scripting** functoids. The following figure shows a mapping from FlattenedCatalog schema to CategorizedCatalog schema.  
  
 ![ValueMappingFunctoid](../core/media/valuemappingvsvaluemappingflattening1.jpg "ValueMappingVsValueMappingFlattening1")  
  
 Configure the functoids with desired input parameters; configure the Scripting functoids (S1, S2, and S3) as follows. Also, set the **TestMap Input Instance** property to the respective input (XML) file.  
  
 The script for S1 is as follows:  
  
```  
public bool IsPetProduct(string SKU)  
{  
     return SKU.StartsWith("88");  
}  
```  
  
 The script for S2 is as follows:  
  
```  
public bool IsGroovyProduct(string SKU)  
{  
     return SKU.StartsWith("89");  
}  
  
```  
  
 The script for S3 is as follows:  
  
```  
public bool IsOtherProduct(string SKU)  
{  
     return !IsGroovyProduct(SKU) && !IsPetProduct(SKU);  
}  
```  
  
 The input file is as below:  
  
```  
<ns0:FlattenedCatalog xmlns:ns0="http://ValueMappingFunctoid">  
  <Product Name="Stapler" SKU="1929383" Price="5.95" />   
  <Product Name="Tape" SKU="6433400" Price="3.50" />   
  <Product Name="Disco Ball" SKU="8900230" Price="49.99" />   
  <Product Name="Thumbtack" SKU="7002399" Price="0.01" />   
  <Product Name="Solar-Powered Pet Groomer" SKU="8802222" Price="229.15" />   
  </ns0:FlattenedCatalog>  
  
```  
  
 After you run a test map operation, you get the following output:  
  
```  
<ns0:CategorizedCatalog xmlns:ns0="http://ValueMapping">  
  <PetProduct Name="Solar-Powered Pet Groomer" SKU="8802222" Price="229.15" />   
  <GroovyProduct Name="Disco Ball" SKU="8900230" Price="49.99" />   
  <OfficeProduct Name="Stapler" SKU="1929383" Price="5.95" />   
  <OfficeProduct Name="Tape" SKU="6433400" Price="3.50" />   
  <OfficeProduct Name="Thumbtack" SKU="7002399" Price="0.01" />   
  </ns0:CategorizedCatalog>  
```  
  
## Using Value Mapping (Flattening) Functoid  
 In this scenario, Catalog is the source schema and FlattenedCatalog is the destination schema. Now, map a non-flattened Catalog message into the flattened FlattenedCatalog message using **Value Mapping (Flattening)** and **Logical** functoids. The following figure shows a mapping from Catalog schema to FlattenedCatalog schema.  
  
 ![Value Mapping &#40;Flattening&#41;](../core/media/valuemappingvsvaluemappingflattening2.jpg "ValueMappingVsValueMappingFlattening2")  
  
 Configure the functoids with desired input parameters, and also set the **TestMap Input Instance** property to the respective input (XML) file.  
  
> [!NOTE]
>  The first input parameter of every **Equal** functoid is its incoming link. Configure the second input parameters for E1, E2, and E3 as constants Name, SKU, and Price, respectively.  
  
 The input file is as below:  
  
```  
<ns0:Catalog xmlns:ns0="http://ValueMappingFunctoid">  
  <Product>  
  <Field Name="Name" Value="Stapler" />   
  <Field Name="SKU" Value="1929383" />   
  <Field Name="Price" Value="5.95" />   
  </Product>  
  <Product>  
  <Field Name="Name" Value="Tape" />   
  <Field Name="SKU" Value="6433400" />   
  <Field Name="Price" Value="3.50" />   
  </Product>  
  <Product>  
  <Field Name="Name" Value="Disco Ball" />   
  <Field Name="SKU" Value="8900230" />   
  <Field Name="Price" Value="49.99" />   
  </Product>  
  </ns0:Catalog>  
```  
  
 After you run a test map operation, you get the following output:  
  
```  
<ns0:FlattenedCatalog xmlns:ns0="http://ValueMappingFunctoid">  
  <Product Name="Stapler" SKU="1929383" Price="5.95" />   
  <Product Name="Tape" SKU="6433400" Price="3.50" />   
  <Product Name="Disco Ball" SKU="8900230" Price="49.99" />   
  </ns0:FlattenedCatalog>  
```  
  
## See Also  
 [Value Mapping Functoid](../core/value-mapping-functoid.md)   
 [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md)