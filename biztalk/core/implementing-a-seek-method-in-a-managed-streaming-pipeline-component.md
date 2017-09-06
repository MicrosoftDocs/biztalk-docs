---
title: "Implementing a Seek Method in a Managed Streaming Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline interfaces, IStream interface"
  - "pipeline components [custom], code samples"
  - "IStream interface"
  - "Seek method"
ms.assetid: 2e546c41-822d-4e22-a8f6-8959072ef3d2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing a Seek Method in a Managed Streaming Pipeline Component
The native **IStream** interface does not provide a method to check the current stream position, so the messaging engine uses the following **Seek** method.  
  
```  
pStream->Seek(0, STREAM_SEEK_CUR, &pNewPosition);  
```  
  
 This method does not move the stream pointer; instead it queries the current position. So if you implement a pipeline component that works with a nonseekable stream, you can use the **Stream.Seek** method as in the following example.  
  
## Example  
  
```csharp  
override public long Seek(long offset, SeekOrigin origin)  
{  
   long pos = -1;  
  
   switch(origin)  
   {  
      case SeekOrigin.Begin :  
         pos = offset;  
         break;  
      case SeekOrigin.Current :  
         pos = Position + offset;  
         break;  
      case SeekOrigin.End :  
         break;  
   }  
  
   // We generally disallow seeking of the stream  
   // However, in unmanaged code, many people use Seek(0,CURR) to retrieve    // the current position  
   // Special case (that is, if Seek does not change position, do not   
   // throw an exception)  
   if (pos==Position)  
   {  
      return pos;  
   }  
   else  
   {  
      throw new NotSupportedException("ForwardOnlyEventingReadStream does not support Seek()");  
   }  
}  
```  
  
## See Also  
 [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md)