---
title: Navigating Group Overview - Query using NVDA screen reader
description: This document helps the user navigate Group Overview - New Query using NVDA screen reader
author: msjaydeep
ms.author: jaah
manager: dougeby
ms.date: 05/29/2020
ms.topic: accessibility
ms.prod: biztalk-server

#ROBOTS:

ms.reviewer:
ms.suite:
ms.tgt_pltfrm:
ms.assetid:
ms.custom:
---

# Navigating and creating New Query in Group Overview

This guidance is for the 'New Query' tab in in 'Group Overview' section of BizTalk Administration Console

## Elements in New Query tab

The New Query Tab has the following elements

- A query expression exposed as a data grid (or a table) called Query table where a user can define the query, this is the place where we create a query.
- There are 3 buttons besides the query. They are 'Run Query', 'Save As…' and 'Open Query…'
- There are menu buttons/close tab buttons and collapsed tab buttons on the top area.

## Columns in the Query table

There are 3 columns in the Query table

1. Field Name
2. Operator
3. Value

## Rows in Query Table

### Guidance on setting up Query Expression and How NVDA reads a row and cells

First Row

The first Row for column 'Field Name' is 'Search For' and column 'Operator' should be 'Equals'
Value of 3rd Column must be chosen out of the many options provided in the drop down.

This cell is read by NVDA as
"Combo box collapsed search for row, value selected" when no value is chosen, once a value is chosen, the chosen value is read with the row and column details.

Second row or more rows can be used to filter the results further

This filter can be changed or more filters can be added based on the query. second row onwards, first column lists the available filters based on current query and filter 'Maximum Matches' is also available for all queries.

By default after running the query 2nd row is filled by Filter 'Maximum Matches' with Value 50.

The 2nd column operator is also combo box and its options change based on type of filter chosen.

The NVDA announces a cell value as

'Cell value' combo box 'Cell value' collapsed
On change of a row, row or column is also announced by the screen reader.
