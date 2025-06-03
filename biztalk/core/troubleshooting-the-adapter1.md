---
description: "Learn how to identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards EnterpriseOne."
title: "Troubleshoot the JD Edwards EnterpriseOne adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-general
---
# Troubleshoot the Adapter

This topic contains information to help you identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for JD Edwards EnterpriseOne.  
  
## Cannot use wildcards in send port properties
  
 Adapter for JD Edwards Enterprise One does not support using wildcards in the following send port property fields:  
  
-   Username  
  
-   JDE Environment  
  
-   Host  
  
-   Port  
  
-   Java_Home  
  
-   JDE JAR Files  
  
-   Security Server Name  
  
-   Service Name Connect  
  
-   Data Source Name  
  
-   Database Owner  
  
-   Database Server Name  
  
-   Database Type  
  
-   Physical Database Name  
  
## Connecting to Oracle database
  
 When using Oracle database with JD Edwards you must modify the jdeinterop.ini file. Using Single-Sign-On the [JDBj-ORACLE] section defines Oracle tnsnames location; the database parameter must be used; and the SQLNET.ORA file must be present on the BizTalk Server computer (this should be included with the Oracle Client).  
  
 Add the following to the jdeinterop.ini file:  
  
1.  Under [JDBj-ORACLE]:  
  
    ```  
    tns=c:\Oracle\ora92\network\Admin\tnsnames.ora  
    ```  
  
2.  Under [JDBj-BOOTSTRAP DATA SOURCE]:  
  
    ```  
    database=sys810 [hardcode the database name. This information is available in the JDE.ini file on the JD Edwards computer.]  
    ```  
  
## See Also
  
 [Add the adapter, and create the artifacts](../core/adding-biztalk-adapter-for-jd-edwards-enterpriseone.md)   
 [Troubleshooting JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)
