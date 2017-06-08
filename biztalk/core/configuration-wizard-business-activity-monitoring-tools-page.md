---
title: "Configuration Wizard, Business Activity Monitoring - Tools Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.config.wizard.bam.runtime"
ms.assetid: 6e84dfe8-6ea6-42a0-9f71-02da594aead3
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration Wizard, Business Activity Monitoring - Tools Page
Use the **Business Activity Monitoring - Tools** page to configure the server with monitoring tools for business users.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable Business Activity Monitoring tools**|Select **Enable Business Activity Monitoring tools** to enable the tools.|  
|**Enable Analysis Services for BAM aggregations**|Select **Enable Analysis Services for BAM aggregations** to provide tracking information for BAM alerts.|  
|**Data stores**|The Data stores list provides an editable view of the server name and databases used for BAM tools.|  
  
 Use the **Business Activity Monitoring - Alerts** page to configure subscription-based notification services.  
  
> [!NOTE]
>  BAM alerts require BAM tools to be enabled.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable SQL Notification Services for BAM alerts**|Select **Enable SQL Notification Services for BAM alerts** to enable BAM alerts.|  
|**Windows service**|The Windows service list provides an editable view of the account used to run the BAM Notification Service.|  
|**BAM Alerts SMTP Server**|Type the name of the SMTP server that will be used to send the BAM alerts.|  
|**BAM Alerts File Location**|Type the name of the network share that will be used to store the BAM alerts. **Note:**  You will need to manually create this share before BAM alerts will store the files.|  
|**SQL Server for Alerts Databases**|Type the name of the SQL server that will be used for the Alerts database.|  
|**Prefix for Alerts Database Names**|Type a prefix that will be used for the Alerts databases.|  
  
## See Also  
 [Installation Overview for BizTalk Server 2013 and 2013 R2](Installation%20Overview%20for%20BizTalk%20Server%202013%20and%202013%20R2.md) 
 [Getting Started](../core/getting-started-with-biztalk-server.md)