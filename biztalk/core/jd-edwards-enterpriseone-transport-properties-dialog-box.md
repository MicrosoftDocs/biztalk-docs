---
title: "JD Edwards EnterpriseOne Transport Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "JDE"
helpviewer_keywords: 
  - "Transport Properties dialog box [JD Edwards EnterpriseOne adapters"
ms.assetid: 6a37eeb2-af91-4f58-9699-7a7cbe296862
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# JD Edwards EnterpriseOne Transport Properties Dialog Box
Use the JD Edwards EnterpriseOne Transport Properties dialog box to set the adapter-required properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Adapter Required Properties**||  
|Host|Type the name of the host server computer (for example, `actsvr1`).<br /><br /> -or-<br /><br /> Type the IP address of the computer (for example, `123.456.0.789`).|  
|JAVA_HOME|Type the complete path to your JDK installation (for example,<br /><br /> `C:\jdk1sdk1.4.2_07`).|  
|JDEdwards Environment|Type the name of an environment in JD Edwards EnterpriseOne (for example, `DV7333`).<br /><br /> DV7333 is a common name for the development environment; PY7333 is common for the prototype environment; and PD7333 is common for the production environment.|  
|JDEdwards JAR files|Enter the complete path and file name for each of the JAR files:<br /><br /> -   Connector.jar<br />-   Kernel.jar<br />-   JDEJAccess.jar<br /><br /> Each jar file must be separated with a semi-colon (;) and no space (for example:<br /><br /> `<c:>\Connector.jar;<c:>\Kernel.jar;`).|  
|Password|Type a user password. If you do not useSingle Sign-On (SSO), you must set credential parameters for BizTalk Adapter for JD Edwards EnterpriseOne to access the server system. The password corresponds to the user name. The password determines the privileges that you are granted when accessing the database.|  
|Port|Type the numerical identifier of the send or receive port (for example, `6009`).|  
|User Name|Type the name of the user, and click **OK**.|  
|**Bootstrap Data Source Required Properties**||  
|Data Source Name|Type the name of the data source. This name is mandatory for all data types.|  
|Database Owner|Type the name of the database owner|  
|Database Server Name|Type the name of the database server|  
|Database Server Port|Type the identifying number of the database server port.|  
|Database Type|Type a single character for the database type. For example:<br /><br /> **I** - iSeries<br /><br /> **O** - Oracle<br /><br /> **S** - SQL Server<br /><br /> **L** - SQL Server OLEDB<br /><br /> **W** - UDB|  
|Physical Database Name|Type the name of the physical database. This name is mandatory for all database types.|  
|**Concurrency Control**||  
|Max Concurrent Calls|Type a numeric value for the **Max Concurrent Calls**. This number represents the maximum number of concurrent calls, for example, **10**.<br /><br /> The default value for this field is 5.|  
|**Refresh Agent**||  
|Refresh Agent|Select **Yes** for the **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.<br /><br /> For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.|  
|**Security Server**||  
|Security Server Name|Type the name of the security server. This field is optional and defaults to the JD Edwards server host.|  
|Service Name Connect|Type the port number used by the security server and object configuration mapping (OCM). Default is the JD Edwards server port.|  
|**Single Sign-On**||  
|Affiliate Application|Select the affiliate application from the drop-down list only if you are using Single Sign-On (SSO).|  
|Use SSO|Select **Yes** if you are using SSO; a password is not required in this case.|  
  
## See Also  
 [Security in BizTalk Adapter for JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)   
 [Creating Affiliate Applications](../core/creating-affiliate-applications4.md)   
 [UI Reference for BizTalk Adapter for JD Edwards EnterpriseOne](../core/ui-reference-for-biztalk-adapter-for-jd-edwards-enterpriseone.md)