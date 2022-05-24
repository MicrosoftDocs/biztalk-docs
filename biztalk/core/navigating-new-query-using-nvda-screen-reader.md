---
title: Use a screen reader to create new queries
description: Learn how to use NVDA screen reader to navigate BizTalk Server Administration console. Create new queries and add filters to results. 
author: msjaydeep
ms.author: jaah
manager: dougeby
ms.date: 05/22/2022
ms.topic: how-to
ms.custom: kr2b-contr-experiment
ms.prod: biztalk-server

#ROBOTS:

ms.reviewer:
ms.suite:
ms.tgt_pltfrm:
ms.assetid:
---

# Use the NVDA screen reader to create queries in BizTalk

This article provides information on using the NonVisual Desktop Access (NVDA) screen reader to manage BizTalk Server Administration console. The following instructions will help you to navigate the **New query** tab in the **Group overview** page using NVDA.

## The new query tab

You can use the **New query** tab to perform the following:

- To create queries to view more information on BizTalk artifacts, such as messaging and orchestration instances.


  - **Run query**: Executes queries you create.
  - **Save as**: Saves your queries to a `.btq` file. This is stored locally on the BizTalk Server.
  - **Open query**: Opens `.btq` queries you save and displays results.

- To filter data so that it only shows messaging instances, orchestrations instances, suspended instances, or other preferences. Filtered results are displayed in a table.

- To create new queries, switch tabs, and close or collapse the query editor. Then use the menu in the **New query** tab.

## Columns in the query table

The query table contains three columns:

- Field name
- Operator
- Value

## Rows in the query table

As you add filters to your queries, new rows are added to your query tables. Filters help expand your data options:

- First Row: In the **Field name** column, select **Search for**, and then select **Equals** in the **Operator** column. In the third column, select what you want to see:
  - All in-progress service instances
  - Running service instances
  - Suspended service instances
  - Messages
  - Subscriptions
  - Tracked message events
  - Tracked service instances

  NVDA reads the row as follows:
  
  - When no value is selected, it states: "Combo box collapsed search for row, value selected."
  - When a value is selected, that value gets read, along with the row and column details.

- Second and additional rows: The more rows you add to your queries, the more you filter your results. Filters can be changed or added, depending on your query options.

  Starting with the second and later rows, the first column lists the available filters based on the current query. By default, the **Maximum matches** filter is selected, and set to `50`. You can change this value.

  NVDA reads the row as follows:

  - The second column operator is a combo box. By default, NVDA states: "'Cell value' combo box 'Cell value' collapsed."
  - When you change the value of a row or column, the new value is announced.

## Next steps

- [Using the Administration Console Query Tab](using-the-administration-console-query-tab.md)
- [Search for Tracked Message Events](how-to-search-for-tracked-message-events.md)
- [Search for Tracked Service Instances](how-to-search-for-tracked-service-instances.md)
