---
title: "Running the SQL Adapter Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13566d08-7a59-4065-b0d7-19ae2765555e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the SQL Adapter Sample
The SQL Adapter sample uses a Windows Forms test client application provided with the Itinerary On-Ramp sample.  
  
 **To run the SQL Adapter sample**  
  
1. If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.  
  
2. In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then start the application named Esb.Itinerary.Test.exe.  
  
3. Clear the **Use WCF Service** check box so that a client-side itinerary can be used.  
  
4. Select the **Two Way Service** option  
  
5. Click the **Load Itinerary** button, and then select one of the sample itineraries located in the folder \Source\Samples\SqlAdapter \Itineraries.  
  
6. Click the **LoadMessage** button, and then select the OrderDoc.xml sample message in the folder \Source\Samples\SqlAdapter \Test.  
  
7. Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.  
  
8. Make sure one row is inserted in the Product table of the GlobalBankESB database.  
  
   For information about how the SQL Adapter sample works, see [How the SQL Adapter Sample Works](../esb-toolkit/how-the-sql-adapter-sample-works.md).