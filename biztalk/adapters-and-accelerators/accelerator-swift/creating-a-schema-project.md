---
title: "Creating a Schema Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67e6278c-a597-4700-80bf-48e37aaa9c05
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Schema Project
To create a schema project:  
  
1.  In Visual Studio, create the SWIFT MX Schema BizTalk project.  
  
2.  Add the appropriate MX schema (downloaded from ISO20022 site), which you wish to test, to this project.  
  
3.  If you want to execute the Message Repair and New Submission functionality for the above MX message, then an Envelope schema corresponding to the above message type also needs to be deployed else proceed to step 6.  
  
    > [!NOTE]
    >  For information on how to generate MX Envelope schemas, please refer to the Form Generator Documentation.  
  
4.  Add the Envelope schema to the SWIFT MX Schema project.  
  
5.  Open the Envelope schema in the BizTalk editor and promote “CorrelationToken” and “IsNewSubmission” properties. Right-click the above fields and click **Promote -> Quick Promotion** to promote these properties.  
  
    > [!NOTE]
    >  For more information on how to promote properties of a schema, please refer to the BizTalk Server documentation.  
  
6.  Create a key file (using Sn –k key.snk), and then assign it to the project to create a strong named assembly.  
  
7.  Build and then deploy the project.