---
description: "Learn more about: Optimizing Database Performance"
title: "Optimizing Database Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a95caf60-f1f5-458f-8a81-0aead88f07be
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing Database Performance
BizTalk Server is an extremely database-intensive application that may require the creation of up to 13 databases in SQL Server. Because one of the primary design goals of BizTalk Server is to ensure that no messages are lost, BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction. Therefore, database performance is paramount to the overall performance of any BizTalk Server solution.

 This section describes general methods for maximizing SQL Server performance as well as methods for maximizing database performance that are specific to a BizTalk Server environment.

## In This Section

-   [Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)

-   [Post-Configuration Database Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)

-   [Optimizing Filegroups for the Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md)

-   [BizTalk Server MessageBox Database Filegroups SQL Script](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)

-   [Monitoring SQL Server Performance](../technical-guides/monitoring-sql-server-performance.md)
