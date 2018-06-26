---
title: "Poll Oracle E-Business Suite using the WCF service model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96670a39-4fec-49bf-85d1-947b1a1bc750
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll Oracle E-Business Suite using the WCF service model
You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive polling-based messages from the Oracle database. The adapter provides two ways of polling the Oracle database:  
  
- **Using SELECT statements**. You can specify a simple SELECT statement to poll the Oracle database. The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.  
  
- **Using stored procedures**. You can specify a stored procedure to poll the Oracle database. The adapter executes the stored procedure at specified intervals and returns the result to the adapter clients.  
  
  The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database. While the polling statement for the first approach is a simple SELECT statement, the polling statement for the stored procedure approach is a request message that executes the stored procedure. Adapter clients specify the polling statement, for either approach, for the **PollingInput** binding property. For more information about the binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
  The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure.  
  
## In This Section  
  
-   [Poll Oracle E-Business Suite using SELECT statement with the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-service-model.md)  
  
-   [Poll Oracle E-Business Suite using stored procedures with the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures-with-the-wcf-service-model.md)  
  
## See Also  
 [Develop Oracle E-Business Suite applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)