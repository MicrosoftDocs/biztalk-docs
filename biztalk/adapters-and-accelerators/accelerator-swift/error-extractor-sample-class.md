---
title: "Error Extractor Sample Class | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Error Extractor Sample class"
  - "errors, Error Extractor Sample class"
ms.assetid: d0d59b21-d80a-4466-a77a-1d3b7df1bc2a
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error Extractor Sample Class
The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] disassembler serializes errors to an XML object, and attaches the XML object to the error section of a multipart message. The disassembler then publishes the failed message to the MessageBox database just as it would a valid message. Therefore, failed messages carry error details into the MessageBox database. You can use the Error Extractor Sample Class to extract the error details from a failed message, and generate one file that has the error details and another file that has the original message.  
  
> [!IMPORTANT]
>  The Error Extractor Sample Class is sample code in the SDK. It is not intended for use in production.  
  
 To use the Error Extractor Sample Class, you must create an orchestration to process the failed message. This orchestration includes steps to extract the body of the failed message, extract the error part of the failed message, and then write the body and the error part to separate XML files. The orchestration represents each of these steps in an expression stage that calls one or more of the following methods in the Error Extractor Sample Class:  
  
## GetBodyPartAsString method  
 This method returns a string that contains the XML found in the body part of the XLANG message 'xm'. The method expects the XLANG message 'xm' to contain a body part called "BodySegment." Therefore, you must declare 'xm' in the calling orchestration with this body part name. If "BodySegment" does not exist as a part of 'xm', **GetBodyPartAsString** throws an exception.  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetBodyPartAsString(XLANGMessage xm);  
```  
  
## GetErrorPartAsString method  
 This method returns a string that contains the XML found in the error part of the XLANG message 'xm'. The method expects the XLANG message 'xm' to contain an error part called "ErrorSegment." Therefore, you must declare 'xm' in the calling orchestration with this error part name. If "ErrorSegment" does not exist as a part of 'xm', **GetErrorPartAsString** throws an exception.  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetErrorPartAsString(XLANGMessage xm);  
```  
  
## WriteToFile method  
 This method writes the string from the *message* parameter to the file specified by the *filePath* parameter.  
  
```  
SWIFTErrorExtractor.ErrorExtractor.WriteToFile(string filePath, string message);  
```  
  
 A4SWIFT Setup installs the Error Extractor Sample Class (SWIFTErrorExtractor.dll) as part of the A4SWIFT SDK in \<*drive*>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial\SWIFTErrorExtractor. This folder also includes the source code for the sample class (ErrorExtractor.cs).  
  
 To call SWIFTErrorExtractor.dll from the orchestration, you must publish the .dll file to the global assembly cache.  
  
## See Also  
 [Tools](../../adapters-and-accelerators/accelerator-swift/tools.md)