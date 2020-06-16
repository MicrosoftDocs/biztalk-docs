---
title: See and query group overview information using NVDA screen reader
description: This document helps the user navigate Group Overview - New Query using NVDA screen reader
author: msjaydeep
ms.author: jaah
manager: dougeby
ms.date: 06/15/2020
ms.topic: accessibility
ms.prod: biztalk-server

#ROBOTS:

ms.reviewer:
ms.suite:
ms.tgt_pltfrm:
ms.assetid:
ms.custom:
---

# Use the NVDA screen reader to query group information in BizTalk Server administration

This guidance is for **Group Overview** > **New Query** tab in BizTalk Server Administration console.

## New Query tab

Use the **New Query** tab to get the following information:

- Create query expressions to get more information on your BizTalk artifacts, such as messaging and orchestration instances. This query is created in a table.
- Use the **Run Query**, **Save As…**, and **Open Query…** buttons to:

  - **Run Query**: Runs the query expression you created.
  - **Save As…**: Saves your query expression to a `.btq` file stored locally on the BizTalk Server.
  - **Open Query…**: Opens the `.btq` query you saved, and shows the results in the console.

- Filter data so it only shows messaging instances, orchestrations instances, suspended instances, and more. You can add more filters by adding new rows to the query expression. As you add more rows to your filter, more data options are available.

  The output is shown as a table.
  
- In the top right hand corner, use the menu buttons to create a new query, switch tabs, and close or collapse the query editor.

## Columns in the Query table

There are three columns in the Query table:

- Field Name
- Operator
- Value

## Rows in Query Table

In your query expression, use rows to filter your data:

- First Row: In the **Field Name** column, select **Search For**, select **Equals** for **Operator** column. In the third Column, select what you want to see:
  - All in-progress service instances
  - Running service instances
  - Suspended service instances
  - Messages
  - Subscriptions
  - Tracked message events
  - Tracked service instances

  NVDA reads the row as: 
  
  - When no value is selected, it states: "Combo box collapsed search for row, value selected".
  - When a value is selected, the chosen value is read with the row and column details.

- Second and additional rows: Add more rows to filter your results. This filter can be changed. Based on your query options, more filters can be added.

  Starting with the second and later rows, the first column lists the available filters based on the current query. By default, the **Maximum Matches** filter is selected, and set to `50`. You can change the filter.

  NVDA reads the row as:

  - The second column operator is also combo box. Its options change based on the filter type you choose. It states: "'Cell value' combo box 'Cell value' collapsed".
  - If you change a row value, then row or column is also announced.

## Next steps

- [Using the Administration Console Query Tab](using-the-administration-console-query-tab.md)
- [Search for Tracked Message Events](how-to-search-for-tracked-message-events.md)
- [Search for Tracked Service Instances](how-to-search-for-tracked-service-instances.md)
