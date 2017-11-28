---
title: "Use namespaces with the WSDL-Proxy in the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 781d20fa-83e3-42fa-866e-5650d5eb71a7
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use namespaces with the WSDL-Proxy in the WCF LOB Adapter SDK
The [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] generates WSDL and proxies for an adapter using values supplied by the developer using the [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)] or specified in code through modification of the SERVICENAMESPACE private variable and/or the `Namespace` property of the adapter.  
  
 The schema types and elements defined within the \<wsdl:types\>\<schema\> use the {OperationNamespace} by default. If a particular type has an overridden TypeNamespace set in the **TypeMetadata** object, that namespace is used for the complex type and/or or element definition.  
  
## Impact on WSDL  
 The following table shows how the different namespaces in a custom adapter affect the corresponding WSDL. In the table, ~{OperationNamespace} is the class namespace mapping of a URI; for example, if {OperationNamespace} is "myscheme://a.b/c", ~{OperationNamespace} will be myscheme.a.b.c.  
  
|WSDL Construct|Syntax|  
|--------------------|------------|  
|WSDL targetNamespace,<br /><br /> Xmlns:ts|{Custom}Adapter.Namespace|  
|\<wsdl:portType\>|{scheme}.~{OperationNamespace}|  
|WSDL Input Message Name|{scheme}.~{OperationNamespace}_{OperationName}_InputMessage|  
|WSDL Output Message Name|{scheme}.~{OperationNamespace}_{OperationName}_OutputMessage|  
|\<wsdl:types\>\<schema\> targetNamespace|{scheme}://{OperationNamespace}|  
|\<element\>\<complexType\>|Use {TypeNamespace} if its value is not null or empty.|  
  
## Impact on Proxy  
 Three different attributes in the proxy are affected by namespaces:  
  
-   [**System.ServiceModel.ServiceContractAttribute**(Name="{scheme}.~{OperationNamespace}", Namespace="{Custom}Adapter.Namespace”]  
  
-   [**System.ServiceModel.MessageContractAttribute**(WrapperName="DivideResponse", WrapperNamespace="{scheme}://{OperationNamespace}", IsWrapped=true)]  
  
-   [**System.ServiceModel.MessageBodyMemberAttribute**(Namespace="{scheme}://{TypeNamespace}", Order=0)]  
  
## See Also  
 [Development best practices using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)