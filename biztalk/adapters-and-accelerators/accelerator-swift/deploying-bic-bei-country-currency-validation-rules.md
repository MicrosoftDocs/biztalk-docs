---
title: "Deploying BIC-BEI-Country-Currency Validation Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e96d416-d5eb-4597-a691-c7dbee33c7d6
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying BIC/BEI/Country/Currency Validation Rules
**To deploy the BIC/BEI/Country/Currency Validation rules:**  
  
1.  The following set of policies, %program files%\Microsoft BizTalk Accelerator for SWIFT\SDK\MX Messages\Base Policies, which are generic and not message-specific, need to be published and deployed separately using the Business Rule Engine Deployment Wizard.  
  
    -   MX_BIC_Master_Policy.xml  
  
    -   MX_BIC_Validation_Policy.xml  
  
    -   MX_BEI_Validation_Policy.xml  
  
    -   MX_DBConnection_Master_Policy.xml  
  
    -   MX_BICPlusIBAN_Validation_Policy.xml  
  
    -   MX_SEPA_Validation_Policy.xml  
  
2.  Before deploying these policies, MX_DBConnection_Master_Policy.xml and MX_BIC_Master_Policy.xml should have the database server name and database name where the Country/Currency values have been stored.  
  
3.  Once the master policies have been modified, publish all polices using the Business Rule Engine Deployment Wizard. Use the following option: Import the policy/vocabulary file to database.  
  
4.  Click Programs, click BizTalk Server \<version\>, click Business Rule Composer, and then deploy the six published polices.