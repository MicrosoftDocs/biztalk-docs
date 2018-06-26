---
title: "Unable to create the entry in the AS2 EDIINT MIC table | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1c75d70-e39e-4465-b32b-db646c059c9b
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unable to create the entry in the AS2 EDIINT MIC table
## Details  
  
|                 |                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| Product Version |                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                           |
|    Event ID     |                                                                                       -                                                                                       |
|  Event Source   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                             |
|    Component    |                                                                                  AS2 Engine                                                                                   |
|  Symbolic Name  |                                                                        AS2MicDataStoreCreateEntryError                                                                        |
|  Message Text   | Unable to create the entry in the AS2 EDIINT MIC table. This could be caused by duplicate AS2-From, AS2-To and MessageID combinations being written to the table.  Error: {0} |
  
## Explanation  
 This error indicates either database connection problems or the row keys already exist in the database table. The full error message should provide information as to why the insert operation failed. The entries in the table are removed after the MDN has been received (whether successful or failed), so this error should never happen after the MDN has been received.  
  
## User Action  
 To resolve this error, check the full error message for information about why the insert operation failed. In SQL, in the EDIINT_MIC table, determine whether there is duplicate AS2-From and AS2-To MessageID combinations. If so, remove them.