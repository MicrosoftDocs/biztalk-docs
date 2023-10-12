---
description: "Learn more about: Define Auto-Growth Settings for Databases"
title: "Define Auto-Growth Settings for Databases"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Define Auto-Growth Settings for Databases
You should set database auto-growth to a fixed number of megabytes instead of to a percentage, especially for the MessageBox and BizTalk Tracking databases. Depending on your BizTalk application and throughput, the MessageBox and Tracking databases can get quite large. If you set auto-growth to a percentage, then the auto-growth can be substantial as well.  
  
## How Instant File Initialization Works  
 When SQL Server increases the size of a file, it must first initialize the new space before it can be used. This is a blocking operation that involves filling the new space with empty pages. SQL Server on Windows supports “instant file initialization.” This can greatly reduce the performance impact of a file growth operation. For more information, see [Database File Initialization](/sql/relational-databases/databases/database-instant-file-initialization). This topic outlines the steps that must be taken to enable instant file initialization.  
  
## Enable Instant File Initialization  
 For steps on enabling instant file initialization, see [Database File Initialization](/sql/relational-databases/databases/database-instant-file-initialization). For creating file groups and moving the BizTalk Server database tables, indexes, and log files into the appropriate file groups, follow the recommendations in the [BizTalk performance optimization guide](../technical-guides/biztalk-server-2013-performance-optimization-guide.md). Ideally the size of files supporting the file groups should be pre-allocated and if possible, set to a static size.  
  
 If the system is new and the static sizes have not been definitively established, then configure files with the **Enable Autogrowth** option and specify file growth **In Megabytes**. The growth increment should generally be no larger than 100 MB (for large files), 10 MB (for medium-sized files), or 1 MB (for small files).