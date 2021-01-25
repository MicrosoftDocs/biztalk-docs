---
description: "Learn more about: sepdchnk"
title: "sepdchnk2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a060a491-78ba-4882-bd76-641c344bb5d6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# sepdchnk
The **sepdchnk** function gets the function management interface (FMI) chunk size. The application calls this function to obtain the chunk size that should be used on the FMI. For more information on FMI chunking, see [Pacing and Chunking](./pacing-and-chunking1.md).  
  
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
