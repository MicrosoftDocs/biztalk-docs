---
description: "Learn more about: Transformation Without Persisting to the BizTalk Message Box Database"
title: "Transformation Without Persisting to the BizTalk Message Box Database"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Transformation Without Persisting to the BizTalk Message Box Database
In this use case, a call to a Web service performs real-time transformation of a message, based on run-time resolution of the appropriate map to apply, and returns the transformed result. Figure 1 illustrates a schematic view of the process.  
  
 ![Transformation Without Persisting](../esb-toolkit/media/ch3-transformationwithout.gif "Ch3-TransformationWithout")  
  
 **Figure 1**  
  
 **Transforming a message without persisting to the Microsoft BizTalk Server Message Box database**  
  
 The Transformation Service sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case. By using it, you can call the ESB Transformation Service; this enables you to test transformations and mappings as you are developing components and policies in the BizTalk Server Business Rules Engine.  
  
 For more information, see [Installing and Running the Transformation Service Sample](../esb-toolkit/installing-and-running-the-transformation-service-sample.md).  
  
> [!NOTE]
>  Do not confuse the Transformation Service referred to here with the dynamic transformation operations performed by the BizTalk Server Transformation Agent. The Transformation Service is a high-performance Web service that significantly reduces latency by calling directly into BizTalk Server without going through the Message Box database.
