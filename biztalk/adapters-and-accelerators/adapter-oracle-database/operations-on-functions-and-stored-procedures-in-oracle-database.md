---
title: "Operations on functions and stored procedures in Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "REF CURSOR"
  - "packaged functions and procedures"
  - "operations, on functions and stored procedures"
  - "stored procedure"
  - "RECORD type"
  - "overloaded functions and procedures"
ms.assetid: 18072b58-65b2-4da5-9433-ea0da4e2d4f4
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on functions and stored procedures in Oracle Database
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports Oracle functions, procedures, and packages in the following manner:  
  
- **Functions** are surfaced as operations. The name of the operation is the name of the Oracle function. IN, OUT, and IN OUT parameters are supported, as well as, RETURN values.  
  
- **Procedures** are surfaced as operations. The name of the operation is the name of the Oracle procedure. IN, OUT, and IN OUT parameters are supported.  
  
- **Packaged functions and procedures** are surfaced as operations. The name and namespace of the operation (function or procedure) is qualified by the name of the Oracle package. Overloads are supported in packages (see next bullet).  
  
- **Overloaded functions and procedures** in packages are surfaced as operations. Each overloaded function or procedure is surfaced with a string appended to its name that identifies the overload. This string is part of the sequence "overload1", "overload2", "overload3", and so on.  
  
- **REF CURSOR types** are supported for IN, OUT, and IN OUT parameters for procedures and functions, as well as for function RETURN values. For more information, see [Operations on Functions and Procedures with REF CURSOR Parameters](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md).  
  
- **RECORD types** are supported for IN, OUT, and IN OUT parameters for procedures and functions, as well as for function RETURN values. Both simple and complex (nested) RECORD types are supported. [Operations on Functions and Procedures with RECORD Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
  For more information about:  
  
- Invoking an Oracle procedure or function by using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Invoke Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md) and [Invoke Overload Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md).  
  
- Invoking an Oracle procedure or function by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).  
  
- Invoking an Oracle procedure or function by using the WCF channel model, see [Invoke a Function in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md).  
  
- Message structure and SOAP actions used to invoke Oracle procedures and functions, see [Message Schemas for Functions and Procedures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)