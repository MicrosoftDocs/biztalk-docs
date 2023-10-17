---
description: "Learn more about: How to Identify Bottlenecks in the BAM Database"
title: "How to Identify Bottlenecks in the BAM Database"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Identify Bottlenecks in the BAM Database
To identify bottlenecks in the BAM database, perform the following steps:  
  
1.  Ensure that the Active Instances count is not climbing.  
  
2.  Ensure that the SQL-Agent Service is running.  
  
3.  If OLAP Analysis is configured ensure that the BAM_AN_ job is running at periodic intervals.  
  
4.  Ensure that BAM_DM_ (Data Maintenance) job is scheduled to run at periodic intervals.
