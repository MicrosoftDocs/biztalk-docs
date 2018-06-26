---
title: "ErrorRecord Object (OLE DB Provider for DB2)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7da6ac3-80f9-4c81-8115-cdc2866babd4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ErrorRecord Object (OLE DB Provider for DB2)
The **ErrorRecord** object is created by calling the **IErrorRecord** interface on the **ErrorObject** object. An **ErrorObject** is created on any interface on any SNA OLE DB object when an error occurs. The **ErrorRecord** object is used to retrieve additional information when an error occurs.  
  
 The following interface of the **ErrorRecord** object is supported by the current version of Microsoft OLE DB Provider for DB2:  
  
- **IErrorInfo**  
  
  OLE DB interface methods return error information in two ways. The error code returned by an interface method, known as the **return code**, indicates the overall success or failure of a method. Error records provide detailed information about the error, such as a text description of the error, the globally unique identifier (GUID) of the interface that defined the error, and provider-specific error information. Error objects in OLE DB are an extension of the error objects in Automation. They use many of the same mechanisms, and can be used as Automation error objects.  
  
  OLE DB error return codes are of type HRESULT. There are two general classes of return codes: success and warning codes, and error codes.  
  
  Success and warning codes begin with S_ or DB_S_ and indicate that the method successfully completed. The standard OLE DB error codes are defined in the OLEDBERR.H include file.  
  
  If the return code is other than S_OK or S_FALSE, it is likely that an error occurred from which the method was able to recover. For example, **IRowset::GetNextRows** returns DB_S_ENDOFROWSET when it is unable to return the requested number of rows due to reaching the end of the rowset. If a single warning condition occurs, the method returns the code for that condition. If multiple warning conditions occur, the method describes the hierarchy of warning return codes, indicating which warning code should be returned when given a choice between multiple warning return codes.  
  
  Error codes begin with E_ or DB_E_ and indicate that the method failed completely and was unable to do any useful work. For example, **GetNextRows** returns E_INVALIDARG when a null pointer in which the OLE DB provider returns a pointer to an array of row handles (*prghRows*). An exception to this is that some of the methods that return DB_E_ERRORSOCCURRED allocate memory to return additional information about these errors. Consumers must free this memory. For information about which methods allocate memory in this case, see the methods that return DB_E_ERRORSOCCURRED.  
  
  Although error codes can indicate run-time errors, such as running out of memory, they generally indicate programming errors. If multiple errors occur, the code that is returned is provider-specific. If both errors and warnings occur, the method fails and returns an error code.  
  
  All methods can return S_OK, E_FAIL, and E_OUTOFMEMORY. The E_OUTOFMEMORY code applies only to those methods which allocate memory that is returned to the consumer. In some cases, the E_OUTOFMEMORY code might be eliminated by calling the method requesting fewer returned values, such as fewer rows from **GetNextRows**.