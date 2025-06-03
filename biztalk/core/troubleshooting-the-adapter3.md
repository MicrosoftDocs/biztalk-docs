---
description: "Learn how to identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards OneWorld."
title: "Troubleshoot the JD Edwards OneWorld adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-general
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
  
 [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)     
 [Troubleshoot JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)
