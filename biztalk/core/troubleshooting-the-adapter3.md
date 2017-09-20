---
title: "Troubleshooting the Adapter3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters [JD Edwards OneWorld adapters], connecting [Oracle databases]"
  - "JD Edwards OneWorld adapters, troubleshooting"
  - "troubleshooting [JD Edwards OneWorld adapters]"
  - "adapters [JD Edwards OneWorld adapters], troubleshooting"
  - "Oracle databases, connecting [JD Edwards OneWorld adapters]"
ms.assetid: 2dd6a951-f113-4f43-b43f-057a239d05c4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting the Adapter
This topic contains information to help you identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards OneWorld.  
  
## Cannot use wildcards in send and receive port properties  
 Adapter for JD Edwards One World does not support using wildcards in the following property fields:  
  
|Send Port Property|Receive Port Property|  
|------------------------|---------------------------|  
|Username|Event File Path|  
|JDE Environment|Event Target Name prefix|  
|Host||  
|Port||  
|Java_Home||  
|JDE JAR Files||  
  
## Connecting to Oracle database  
 When using Oracle database with JD Edwards you must modify the jdeinterop.ini file. Using Single-Sign-On the [JDBj-ORACLE] section defines Oracle tnsnames location; the database parameter must be used; and the SQLNET.ORA file must be present on the BizTalk Server computer (this should be included with the Oracle Client).  
  
 Add the following to the jdeinterop.ini file:  
  
1.  Under [JDBj-ORACLE], type:  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  Under [JDBj-BOOTSTRAP DATA SOURCE], type:  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## See Also  
 [How to Create Send Ports for JD Edwards OneWorld](../core/how-to-create-send-ports-for-jd-edwards-oneworld.md)   
 [Troubleshooting JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)