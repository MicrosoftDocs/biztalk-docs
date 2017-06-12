---
title: "Business Rule Engine Security Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, business rules"
  - "Business Rules Framework, security"
  - "business rules, security"
ms.assetid: d5df1cd0-112a-4c72-b95d-cbcd1bc6a2c3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Business Rule Engine Security Recommendations
The Business Rule Engine is the runtime component of the Business Rule Framework. With the Business Rule Framework, you can connect highly readable, declarative, semantically rich rules to any business objects (.NET components), XML documents, or database tables. For more information about the Business Rule Framework, see [Creating and Using Business Rules](../core/creating-and-using-business-rules.md). For more information about the Business Rule Engine, see [Rule Engine](../core/rule-engine.md).  
  
 There are no Windows user groups for the Business Rule Engine, only individual accounts. BizTalk Server restricts access to the Business Rule Engine resources by using two SQL Server roles:  
  
 The RE_Admin_Users SQL Server role is for users that need to perform administrative tasks in the Business Rule Engine, such as deploying rules. Members of the RE_Admin_Users SQL Server role include BizTalk administrators.  
  
 The RE_Host_Users group is for all other users of the Business Rule Engine that do not require administrative user rights, and perform tasks such as reading and executing rules. Members of the RE_Host_Users role include the BizTalk_Host_Users role. You can use the SQL Server roles to implement permissions to the Business Rule Engine independent from the BizTalk Server permissions. For more information about the minimum permission needed to use the Business Rule Engine, see [Minimum Security User Rights](../core/minimum-security-user-rights.md). It is recommended you follow these guidelines for securing and deploying the Business Rule Engine in your environment.  
  
-   BizTalk Server gives the account you used to install the update service logon as service rights and adds it to the RE_Host_Users SQL Server role on the Business Rule Engine database. If the account you use for installation is not the same you are going to use for running the update service, you must remove the installation account from the RE_Host_Users SQL Server role.  
  
-   If you use the Update service component, you must install it on all BizTalk runtime computers. In order to retrieve a rule from the Rule Engine database, the update service impersonates the caller of the service.  
  
-   By default, all BizTalk Hosts have the same level of access to rules engine artifacts. There is not per-host segregation of security. You can configure per-policy security by using the rule engine APIs. For more information about how to configure per-policy security, see [Business Rules Framework Security](../core/business-rules-framework-security.md).  
  
## See Also  
 [Ports for the Processing Servers](../core/ports-for-the-processing-servers.md)