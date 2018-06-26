---
title: "How to Select a Live or Archived Data Source | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Management database, archived data"
  - "Management database, real-time data"
  - "HAT, real-time data"
  - "archived data, Management database"
  - "HAT, archived data"
  - "real-time data, HAT"
  - "real-time data, Management database"
  - "archived data, HAT"
ms.assetid: e2325823-22e1-4a1a-865b-15757b215b29
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Select a Live or Archived Data Source
BizTalktracking enables you to access both archived and live data. You select a live or archived data source from the main **BizTalk Server Administration** node BizTalk Server Administration Console.  The default source is live data, retrieved from the BizTalk Management database. If you choose to work with archived data, you must select the appropriate server/s and database/s with which to work.  

-   Archived data: Analyzing archived data enables you to examine trends both in your business and on your system, because you can look as far back as necessary. If you select archived data, you must also select the appropriate SQL Servers and SQL databases that contain the archived data.  

     Archived data is designated by selecting **Connect to an existing tracking database…**.  

-   Live data: Analyzing live data enables you to monitor orchestrations and pipelines, so that you can identify and fix problems in the development or staging environment. Monitoring live data also enables you to correct problems in your system, such as why messages are being suspended.  

     Live data is designated by selecting **Connect to an existing group…**.  

## Prerequisites  
 You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.  

### To select live data  

1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. Click the main  **BizTalk Server Administration** node.  

3. Click **Connect to an existing group…**  

4. In the **SQL Server name** box, type the name of the server that hosts the BizTalk Management database.  

5. In the **Database name** drop-down list box, select **BizTalkMgmtDb**.  

6. Click **OK**.  

### To select archived data  

1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. Click the main  **BizTalk Server Administration** node.  

3. Click **Connect to an existing tracking database…**  

4. In the **SQL Server name** box, type the name of the server that hosts the BizTalk Management database.  

5. In the **Database name** drop-down list box, select **BizTalkMgmtDb**.  

6. Click **OK**.
