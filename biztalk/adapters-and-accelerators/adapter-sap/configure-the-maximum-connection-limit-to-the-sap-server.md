---
description: "Learn more about: Configure the Maximum Connection Limit to the SAP Server"
title: "Configure the Maximum Connection Limit to the SAP Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configure the Maximum Connection Limit to the SAP Server
The Data Provider for SAP enables adapter clients to control the maximum number of connections that can be opened by the provider internally. You can control this by setting the environment variable, CPIC_MAX_CONV.  
  
 For example, if CPIC_MAX_CONV is set to any numerical value, the number of RFC connections opened at any time will be less than or equal to that numerical value.  
  
> [!NOTE]
>  The numerical value will be applicable for every server individually under the process/appdomain which sets this value.  
  
 For example, if an application using Data provider for SAP, has set its environment variable at process level to “x” and connects to two different servers A and B, then the maximum number of connections for both A and B will be “x” respectively.
