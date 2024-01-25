---
description: "Learn more about: Extending the Solution for Capture and Message Repair"
title: "Extending the Solution for Capture and Message Repair"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Extending the Solution for Capture and Message Repair
The MT103 End-to-End Tutorial in this Help shows you how to construct a BizTalk orchestration that subscribes to failed SWIFT messages.  
  
 The orchestration in the MT103 End-to-End Tutorial uses the static methods of a helper class, **ErrorExtractor**, to extract the error part and body from the message as strings. The orchestration then writes the parts to separate files.  
  
 Because the error part of the failed message is a serialization of the **ErrorCollection** constructed by the pipeline component, you can deserialize the collection and use it to automate more of the error reporting and handling. The following Microsoft [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] code fragment illustrates how to deserialize the error message part of a failed message and iterate over the parsing errors in the collection. The code fragment omits namespace qualifications for readability:  
  
```  
// instantiate an appropriate XmlTextReader  
// xm contains the message  
string sError = ErrorExtractor.GetErrorPartAsString(xm);  
StringReader sRdr = new StringReader(sError);  
XmlTextReader xRdr = new XmlTextReader(sRdr);  
  
// deserialize the collection  
ErrorCollection eC = ErrorCollection.GetErrorCollection(xRdr);  
  
// loop over the parsing errors in the collection  
IEnumerator pEnum = eC.GetParseErrorEnumerator();  
while(pEnum.MoveNext())   
{  
  // pEnum.Current() returns a ParseError object for processing  
}  
  
```  
  
 The **ErrorCollection** includes methods for iterating over errors by type as well as for iterating over all of the errors in the collection. For more information about the **ErrorCollection**, see ErrorCollection Members.  
  
## See Also  
 [Failed Messages and ErrorCollection Objects](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)
