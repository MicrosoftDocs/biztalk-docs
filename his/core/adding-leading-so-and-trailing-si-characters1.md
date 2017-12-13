---
title: "Adding Leading SO and Trailing SI Characters1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84d09b8c-e339-417d-a9ea-4109d9d6e845
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding Leading SO and Trailing SI Characters
For PIC G formatted strings, you can instruct the Transaction Integrator (TI) run-time environment to add a leading shift-out (SO) character and a trailing shift-in (SI) character by selecting the **Add Leading SO and Trailing SI** check box on the string's **COBOL Definition** tab (property page) in TI Project.  
  
 If the **Add Leading SO and Trailing SI** check box is selected, the TI run-time environment handles two additional bytes in the mainframe data structure used for describing the double-byte character set (DBCS) string. When it formats a message sent to the mainframe, the TI run-time environment adds the leading SO and trailing SI bytes. When it interprets a message received from the mainframe, the TI run-time environment discards the leading SO and the trailing SI bytes.  
  
 The dimension value of the PIC G string always specifies the number of double-byte DBCS characters in the strings, regardless of the presence or absence of the surrounding SO and SI characters.  
  
 The use of this automatic SO and SI handling is hidden from the client application. However, the mainframe application must ensure that the appropriate PIC X declarations surround the declaration of the PIC G string.  
  
 TI Project generates the appropriate declarations for the surrounding SO and SI bytes, as shown in the following sample code:  
  
```  
01     A-SOSI-WRAPPED-DBCS.  
       05  LEADING-SO-1                            PIC X.  
       05  MY-DBCS-STRING                          PIC G(80).  
       05  LEADING-SI-1                            PIC X.  
  
```  
  
 The Import COBOL Wizard in TI Project does not set the option to add leading SO and trailing SI bytes. In other words, the Import COBOL Wizard places no significance on the presence of PIC X declarations surrounding a PIC G string. If an existing mainframe transaction program (TP) uses COBOL declarations that contain explicit declarations for SO and SI characters that wrap PIC G strings, you must manually modify the interface created by the Import COBOL Wizard.