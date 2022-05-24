---
title: Use NVDA screen reader to create new queries in BizTalk Server Administration console
description: Learn how to use NVDA screen reader to create new queries in BizTalk Server Administration console.
author: msjaydeep
ms.author: jaah
manager: dougeby
ms.date: 05/22/2022
ms.topic: conceptual
ms.custom: kr2b-contr-experiment
ms.prod: biztalk-server

#ROBOTS:

ms.reviewer:
ms.suite:
ms.tgt_pltfrm:
ms.assetid:
---

# Use NVDA screen reader to create new queries in BizTalk Server administration

This article provides information on using NVDA screen reader to navigate the **Group Overview** > **New Query** tab in the BizTalk Server Administration console.

## New Query tab

Use the **New query** tab for the following:

- To create queries to view more information on BizTalk artifacts, such as messaging and orchestration instances.


  - **Run query**: Executes queries you create.
  - **Save as…**: Saves your queries to a `.btq` file. This is stored locally on the BizTalk Server.
  - **Open query…**: Opens `.btq` queries you save and displays results.

- To filter data so that it only shows messaging instances, orchestrations instances, suspended instances, or other preferences. Filtered results are displayed in a table.
  
- To create new queries, switch tabs, and close or collapse the query editor.


  - Use the menu buttons in the top right-hand corner of the **New Query** tab.

## Columns in the Query table

There are three columns in the Query table:

- Field name
- Operator
- Value 

## Rows in Query Table

You can add filters to your queries by adding new rows. As you add filters, you expand your data options:

- First Row: In the **Field Name** column, select **Search For** and then select **Equals** in the **Operator** column. In the third Column, select what you want to see:
  - All in-progress service instances
  - Running service instances
  - Suspended service instances
  - Messages
  - Subscriptions
  - Tracked message events
  - Tracked service instances

  NVDA reads the row as follows:
  
  - When no value is selected, it states: "Combo box collapsed search for row, value selected".
  - When a value is selected, that value gets read, along with the row and column details.

- Second and additional rows: The more rows you add to your queries, the more you filter your results. Filters can be changed or added, depending on your query options.

  Starting with the second and later rows, the first column lists the available filters based on the current query. By default, the **Maximum Matches** filter is selected, and set to `50`. You can change this value.

  NVDA reads the row as follows:

  - The second column operator is a combo box. As a default, NVDA states: "'Cell value' combo box 'Cell value' collapsed".
  - When you change the value of a row or column, the new value is announced.

## Next steps

- [Using the Administration Console Query Tab](using-the-administration-console-query-tab.md)
- [Search for Tracked Message Events](how-to-search-for-tracked-message-events.md)
- [Search for Tracked Service Instances](how-to-search-for-tracked-service-instances.md)
