---
title: "PeopleSoft Transport Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PeopleSoft"
helpviewer_keywords: 
  - "PeopleSoft Transport Properties dialog box"
ms.assetid: 660f0a0b-e076-4f4e-8b2a-6d976acfc5ce
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PeopleSoft Transport Properties Dialog Box
Use the PeopleSoft Transport Properties dialog box to set the adapter-required properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Adapter Required Properties**||  
|Application server path|Type the path for the PeopleSoft server (for example, `//psserver.domain.com:9000`).|  
|JAVA_HOME|Type the name for the JAVA_HOME location (for example, `<drive:>\jdk1.4.2_08`).|  
|Password|Type the password for this user.|  
|PeopleSoft 8.x JAR files|Type the path for the location of the PeopleSoft JAR files (for example, `<drive:>\JAR_FILES\Peoplesoft_8.4\psjoa.jar`).|  
|User name|Type the name of the user, and click **OK**.|  
|**Additional Parameters**||  
|Database Date Format|Type the format in which you want dates to appear (for example,**YYYY-MM-DD**).<br /><br /> The date has a different format when used as a key.|  
|**Concurrency Control**||  
|Max Concurrent Calls|Type a numeric value for the **Max Concurrent Calls**. This number represents the maximum number of concurrent calls, for example, 200.<br /><br /> The default value for this field is -1, meaning no protection occurs.|  
|**Connection**||  
|Maximum number of sessions|Type a number to represent the maximum number of sessions.<br /><br /> The default number of connections is 40.|  
|**Refresh Agent**||  
|Refresh Agent|Select **Yes** for the **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.<br /><br /> For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Adapter Wizard for selection.|  
|**Single Sign-On**||  
|Affiliate Application|Select the affiliate application from the list only if you are using Single Sign-ON (SSO).|  
|Use SSO|Select **Yes** if you are using SSO; a password is not required in this case. **Note:**  If you already entered a password and you want to use Single Sign-On, right-click the Password field and select **Nullify Password**.|  
  
## See Also  
 [UI Reference for BizTalk Adapter for PeopleSoft Enterprise](../core/ui-reference-for-biztalk-adapter-for-peoplesoft-enterprise.md)