---
title: "Variable-length Tables and CICS LINK1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4736100b-55f6-408a-9234-ee7593d693e2
caps.latest.revision: 4
---
# Variable-length Tables and CICS LINK
When an OCCURS clause describes a variable-length table in the CICS LINK environment, the storage that the table uses on the host varies depending on the value of the length specifier. COBOL handles this storage automatically on the host, but for Transaction Integrator (TI) to determine where in the buffer to place data sent to the host and where to unpack data from the host, you must give it the value of the length specifier variable on which the table size depends.  
  
 Any data that follows a variable-length table must be correctly offset in the buffer immediately following the table, regardless of the maximum length of the table. TI must have the length specifier value for a variable-length table both when it packs the buffer to be sent and when it unpacks the buffer that is received.  
  
 If an OCCURS clause describes a variable-length table, you must specify the table and the length specifier that controls the table length as input/output in TI Project. The TI run-time environment must be able to detect the length both when the buffer is sent to the host and when it is received from the host. When you import COBOL or manually create a method that describes a variable-length table in TI Project, this restriction is enforced.  
  
> [!NOTE]
>  Information in this topic also applies to arrays.  
  
## See Also  
 [Defining a Variable-length Table with the  OCCURS DEPENDING Clause](../HIS2010/defining-a-variable-length-table-with-the-occurs-depending-clause.md)