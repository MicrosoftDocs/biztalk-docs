---
description: "Learn more about: Develop Oracle E-Business Suite applications using the WCF Channel Model"
title: "Develop Oracle E-Business Suite applications using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75bb6de1-e11a-4377-af13-e1cb954aaf3f
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop Oracle E-Business Suite applications using the WCF Channel Model
You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] by sending XML messages directly over a channel instance created with the Oracle EBS Binding.  
  
 One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the Oracle E-Business Suite. This control comes from the fact that in the WCF channel model, you directly control the contents of the messages that you send over the channel.  
  
 In certain scenarios, this extra level of control can be beneficial. For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message. The only columns that are required are those with “nillable=false” in the WSDL. The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema.  
  
 The topics in this section explain how to perform operations on the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] by using the WCF channel model.  
  
## In This Section  
  
-   [Overview of the WCF channel model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [Create a channel using Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-channel-using-oracle-e-business-suite.md)
  
-   [Run an insert operation on an interface table in Oracle E-Business Suite using the WCF channel model](../../adapters-and-accelerators/adapter-oracle-ebs/insert-on-an-interface-table-in-oracle-ebs-using-the-wcf-channel-model.md)  
  
-   [Poll Oracle E-Business Suite using SELECT statement with the WCF channel model](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model.md)
  
## See Also  
[Develop your Oracle E-Business Suite applications](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)
