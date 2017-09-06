---
title: "Accessing SOAP Headers in Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SOAP headers, pipelines"
  - "SOAP headers, properties"
  - "pipelines, SOAP headers"
ms.assetid: a2fb074e-0fde-487e-a6ec-7e2b543b7c8b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Accessing SOAP Headers in Pipeline Components
You can access SOAP header context properties in pipeline components. You use a combination of the context property name and the target namespace **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**.  
  
 The following code example gets the request SOAP header in a receive pipeline component for the property **OrigDest**:  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
   {  
   string stringVar = inmsg.Context.Read("OrigDest",    "http://schemas.microsoft.com/BizTalk/2003/SOAPHeader").ToString();  
   }  
   catch (Exception ex)  
   {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
   }  
return inmsg;  
}  
```  
  
 For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).  
  
## See Also  
 [SOAP Headers with Published Web Services](../core/soap-headers-with-published-web-services.md)