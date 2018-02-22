---
title: "SQL Server Optimizations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb735b54-595e-4dd0-9e4d-9a5e7a007a78
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SQL Server Optimizations
BizTalk Server is an extremely database intensive application that may require the creation of up to 13 databases in SQL Server. Because one of the primary design goals of BizTalk Server is to ensure that no messages are lost, BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction. Therefore, database performance is paramount to the overall performance of any BizTalk Server solution.  
  
This section describes general methods for maximizing SQL Server performance as well as methods for maximizing database performance that are specific to a BizTalk Server environment. The following links are also good resources: 

- [BizTalk Server: Recommendations for Installing, Sizing, Deploying, and Maintaining a Solution](https://social.technet.microsoft.com/wiki/contents/articles/666.biztalk-server-recommendations-for-installing-sizing-deploying-and-maintaining-a-solution.aspx)

- [BizTalk Server Performance Optimization Guide](biztalk-server-2013-performance-optimization-guide.md)

  
## Next steps
  
-   [Pre-Configuration Database Optimizations](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [Post-Configuration Database Optimizations](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [Optimizing Filegroups for the Databases](../technical-guides/optimizing-filegroups-for-the-databases1.md)