---
title: "Advanced Tab (Application Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15335"
ms.assetid: c67450f7-7a61-48d4-8331-051bdfd95dd7
caps.latest.revision: 4
---
# Advanced Tab (Application Properties)
The **Advanced** tab allows you to set the advanced properties of the application.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Minimum active worker threads**|Type or select the minimum number of worker threads that the HIP runtime maintains. The number of threads must be greater than 0 and fewer than 193. The number cannot exceed the number of **Worker threads** set on the **General** tab property page. The default is **8** threads.|  
|**Cleanup worker threads**|The group of properties controlling thread cleanup.|  
|**When no requests have been queued for**|Type or select the number of seconds the HIP runtime will wait after the last client request has been received before it terminates the threads. The minimum wait is 1 second and the maximum wait is 3600 seconds. The default is **30** seconds.|  
|**Start an additional working thread**|The group of properties controlling when new threads are started.|  
|**When more than** <br /> ***number* requests have been queued**|Type or select the number of requests that must be received before additional worker threads are started. The minimum number of requests is 1, and the maximum number of requests is 99,999. The default is **15** requests. The number of requests cannot exceed the **Maximum queued requests** (set on the **General** tab) multiplied by the **During the previous *number* seconds** (set on this tab).|  
|**During the previous** <br /> ***number* seconds**|Type or select the number of seconds the HIP runtime must wait before starting additional worker threads. The minimum number of seconds is 1, and the maximum number of seconds is 3600. The default is **5** seconds.|  
|**Increase context cache size**|The group of properties controlling the size of the cache of incoming context requests over a period of time.|  
|**When more than** <br /> ***number* contexts have been created**|Type or select the number of contexts that must be created before the HIP runtime increases the size of the cache. The request context is needed to pass the parameters of the request from the listener to a worker thread. The initial cache size is equal to the number of worker threads multiplied by 2, which is normally less than the maximum queue length. If the cache is empty, a new context is created but will be destroyed at the end because there is no place in the cache to put it in. Increasing the cache size allows the HIP runtime to save the context for future reuse to eliminate expensive operations of creating and releasing the context. The cache size can grow up to the maximum queue length. The minimum number of contexts is 1, and the maximum number of contexts is 192. The default is **30** contexts.|  
|**During the previous** <br /> ***number* seconds**|Type or select the number of seconds the HIP runtime must wait before increasing the cache size. The minimum number of seconds is 1, and the maximum number of seconds is 3600. The default is **5** seconds.|  
  
> [!CAUTION]
>  The properties of an application are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the application to function incorrectly.  
  
## See Also  
 [Application](../HIS2010/application2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)