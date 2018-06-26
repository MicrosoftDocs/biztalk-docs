---
title: "SNA Print Server Data Filter API1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dbdfaf09-c4f5-4f94-a80f-2c92d189abf4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNA Print Server Data Filter API
You configure the path to the print data filter DLL. This DLL is used by all sessions actively using the Host Print service. However, the print data filter DLL can specify whether or not it wants a given session's print data passed to it.  

 The entry points to this DLL are listed as follows:  

 [PrtFilterAlloc](../core/prtfilteralloc2.md)  
 Obtains a data buffer in which to pass print data.  

 [PrtFilterFree](../core/prtfilterfree1.md)  
 Indicates that a data buffer obtained previously from the DLL is no longer needed and the DLL can free the memory allocated for this resource.  

 [PrtFilterJobData](../core/prtfilterjobdata2.md)  
 Allows the DLL to manipulate print data.  

 [PrtFilterJobEnd](../core/prtfilterjobend1.md)  
 Informs the DLL that a print job has ended.  

 [PrtFilterJobStart](../core/prtfilterjobstart1.md)  
 Informs the DLL that a new print job has started and enables the DLL to send special data to the Print Server at the start of a job.  

 A description of the example sequence of calls during an ordinary print job is listed below to illustrate how these functions are normally used:  

- **PrtFilterStartJob** is called when a new print job is started. The DLL can return a data buffer with special data that will be sent to the printer (a special banner page or special printer initialization strings, for example) before printing data.  

- **PrtFilterFree** is called if special data was sent in the **PrtFilterStartJob** function and indicates that the data buffer used to pass special data can be freed.  

  The next sequence of function calls is repeated until all of the print data has been sent:  

- **PrtFilterAlloc** is called to allocate a data buffer used to pass print data in the subsequent call to **PrtFilterJobData**.  

- **PrtFilterJobData** is called to pass print data to the DLL for possible modification. This allows the user DLL the opportunity to manipulate the printer data before it is sent to the printer. If the modified print data to be returned requires a larger data buffer or the DLL needs to use a different data buffer for returning data, the DLL may need to allocate a new data buffer to return this data. The DLL may also choose to free the data buffer used to pass the incoming print data if a different data buffer is used to return modified print data. The **PrtFilterFree** function will not be called with the pointer to the original data buffer if a different data buffer is returned by **PrtFilterJobData**.  

- **PrtFilterFree** is called to indicate that the data buffer allocated by **PrtFilterAlloc** for passing incoming data to the **PrtFilterJobData** function can be freed. If a different data buffer was returned by **PrtFilterJobData**, then **PrtFilterFree** would be called to indicate that a data buffer allocated by the DLL used to return modified print data in the **PrtFilterJobData** function can be freed.  

  The final sequence occurs when all of the print data has been processed:  

- **PrtFilterEndJob** is called to indicate the end of the print job and allows the DLL the option to return special data (a trailer page, for example) that should be sent to the printer.  

- **PrtFilterFree** is called if special data was sent in the **PrtFilterEndJob** function and indicates that the data buffer used to pass special data can be freed.
