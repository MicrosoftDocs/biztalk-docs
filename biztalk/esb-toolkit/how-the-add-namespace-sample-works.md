---
title: "How the Add Namespace Sample Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c76a90a9-5898-43b3-98af-ff546dd97153
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the Add Namespace Sample Works
The first, second, and fourth tests use the **Add Namespace** component located in the NamespaceSampleReceivePipeline pipeline. It takes as input a document with no namespace on the root node, such as the following:  

```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```  

 The following table shows the property values set for the **Add Namespace** component.  


|      Property       |  Type   |                          Value                           |
|---------------------|---------|----------------------------------------------------------|
| ExtractionNodeXPath | Static  |                         (empty)                          |
|    NamespaceBase    | Static  |    http://schemas.microsoft.biztalk.esb.test.com/test    |
|   NamespacePrefix   | Static  |                         esbTest                          |
|      Separator      | Static  |                            /                             |
|       XPaths        | Dynamic | /CanonicalOrder/@OrderID&#124;/CanonicalOrder/@OrderDate |

 The property settings shown in the table cause the component to search the XML document by executing the two XPath queries /CanonicalOrder/@OrderID and /CanonicalOrder/@OrderDate (the two queries specified for the **XPaths** property, separated by a "pipe" character). These queries return the values of the **OrderID** and **OrderDate** attributes of the root node of the document; in this example, the two values are "OrderID_0" and "OrderDate_1".  

 The component then uses these values, and the values of the other properties, to construct the new root namespace. It combines the **NamespaceBase**, the **NamespacePrefix**, the **Separator**, and the values from the two XPath queries in the following format:  

```  
xmlns:{NamespacePrefix}="{NamespaceBase}{Separator}{XPaths[1]}{Seperator}  
                         {XPaths[2]}{Separator}...{XPaths[n]}"  
```  

 This produces the new namespace, as shown here:  

```  
xmlns:esbTest="http://schemas.microsoft.biztalk.esb.test.com/test  
               /OrderID_0/OrderDate_1"  
```  

 Therefore, the updated document after processing by the **NamespaceSampleReceivePipeline** pipeline is the following:  

```  
<esbTest:CanonicalOrder xmlns:esbTest=  
    "http://schemas.microsoft.biztalk.esb.test.com/test/OrderID_0  
    /OrderDate_1" OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2">  
```  

## Using the ExtractionNodeXPath Property  
 By default, the **Add Namespace** component uses the root element of the XML document within the message when adding namespace and prefix information. If you want to use only a subset of the XML document as the message body (useful in certain envelope scenarios or when only a portion of an inbound document has relevance), you can set the **ExtractionNodeXPath** property to force the **Add Namespace** component to seek the specified element for use as the resultant message. For example, if you know that a received CanonicalOrder message will have only one **OrderDetails** element that is relevant for consumers of this message contained within it, you can set the **ExtractionNodeXPath** property to specify the path to the **OrderDetails** element. You can see an example of this process in the Add Via Extraction to Pass-through test described earlier.  

> [!NOTE]
>  The **ExtractionNodeXPath** property must be an XPath that returns only one element. The component will raise an exception if the result is not an element or if the XPath query returns more than one element.