---
description: "Learn more about: Using SOAP Headers in Pipeline Components"
title: "Using SOAP Headers in Pipeline Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using SOAP Headers in Pipeline Components
To access the SOAP header context properties in pipeline components, you use a combination of the context property name and target namespace as discussed in [Using SOAP Headers in Orchestrations](../core/using-soap-headers-in-orchestrations.md).  
  
 The following code example sets the request SOAP header in a send pipeline component for a property name **OrigDest**:  
  
```  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
   try  
      {  
       string stringVar = "<?xml version=\"1.0\"?>  
          <OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
             <Origination>Home</Origination>  
             <Destination>Work</Destination>  
          </OrigDest>";  
inmsg.Context.Write("OrigDest","http://schemas.microsoft.com/BizTalk/2003/SOAPHeader", stringVar);  
      }  
   catch (Exception ex)  
      {  
   throw new Exception("Pipeline component exception - " + ex.Message);  
      }  
return inmsg;  
}  
```  
  
 For more information about pipeline components, see [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md).  
  
> [!NOTE]
>  When you consume (call) Web services from an orchestration, the SOAP adapter only supports pass-through style receive and send pipelines. You can use a custom pipeline, but it cannot contain components that modify the body parts of the message. These components include the XML Assembler, XML Disassembler, and XML Validator components.  
  
## See Also  
 [Default Pipelines](../core/default-pipelines.md)   
 [SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md)
