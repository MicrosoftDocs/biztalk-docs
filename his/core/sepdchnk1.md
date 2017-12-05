---
title: "sepdchnk1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa246c1f-f83c-41de-bc82-185719bad72f
caps.latest.revision: 3
---
# sepdchnk
The **sepdchnk** function gets the function management interface (FMI) chunk size. The application calls this function to obtain the chunk size that should be used on the FMI. For more information on FMI chunking, see [Pacing and Chunking](../core/pacing-and-chunking2.md).  
  
## Syntax  
  
```  
  
VOID sepdchnk(  
USHORT *pipesizeptr,  
USHORT *chunksizeptr  
);  
```  
  
#### Parameters  
 *pipesizeptr*  
 Size in bytes of the pipe between the application and the local node.  
  
 *chunksizeptr*  
 Dynamic Access Module (DMOD) chunk size in bytes.  
  
## Remarks  
 The application does not need to use the pipe size returned by this call. (It is included on this call because the local node uses the same call to obtain both the pipe size and the chunk size.)