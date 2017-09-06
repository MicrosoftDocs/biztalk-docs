---
title: "Adapter GetSchema Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c83340c-a775-435c-9633-3a692611e99e
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter GetSchema Method
Suppose the referenced WSDL file contains only schema references and does not contain embedded schemas. In this case, you use the **GetSchema** method of the **IAdapterConfig** interface to load a schema referenced from within a WSDL file.  
  
 In the file adapter sample, modify the code in the **GetSchema** method of AdapterManagement.cs to return any external XSD files that are not included with the WSDL files.  
  
 The following code is from the **GetSchema** method of the AdapterManagement.cs file. It returns null here because the Service1.wsdl file contains embedded schemas. If that were not the case, a string corresponding to an XSD schema file would need to be returned.  
  
```  
/// <summary>  
        /// Acquire externally referenced xsd's  
        /// </summary>  
        /// <param name="xsdLocation">Location of schema</param>  
        /// <param name="xsdNamespace">Namespace</param>  
        /// <param name="XSDFileName">Schmea file name (return)</param>  
        /// <returns>Outcome of acquisition</returns>  
        public Result GetSchema(string xsdLocation,  
                                string xsdNamespace,  
                        out string xsdSchema)   
      {  
            xsdSchema = null;  
            return Result.Continue;  
        }  
```