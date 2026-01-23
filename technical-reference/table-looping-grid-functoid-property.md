---
description: "Learn more about: Table Looping Grid (Functoid Property)"
title: Table Looping Grid (Functoid Property)
TOCTitle: Table Looping Grid (Functoid Property)
ms:assetid: 2e5244a1-2a12-40ed-ad67-b8e7baa3f048
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559418(v=BTS.80)
ms:contentKeyID: 51527054
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Table Looping Grid (Functoid Property)

 

Use the **Table Looping Grid** property to open the **Configure Table Looping Functoid** dialog box, in which you can configure a table of values, known as the "looping grid," associated with the corresponding **Table Looping** functoid.

## Category

General

## Value

The value of this property is the table of values configured in the **Configure Table Looping Functoid** dialog box. This table contains an arbitrary number of rows, configurable while editing the table, and a number of columns specified by the second input parameter to the corresponding **Table Looping** functoid, as configured in the **Configure \<Functoid\> Functoid** dialog box.

Each table cell is configured by using a drop-down list that is identical for each cell, where the entries in the drop-down list are the third through the last input parameters to the corresponding **Table Looping** functoid, as configured in the **Configure \<Functoid\> Functoid** dialog box. These input parameters consist of a combination of the links into the functoid and any constant input parameters that have been defined. If link input parameters have been given a **Label** property value, that value is shown in the drop-down lists; otherwise, the value of the **Link Source** property is shown (generally, the former is friendlier than the latter). Constant input parameters are shown according to their constant value.

The **Configure \<Functoid\> Functoid** dialog box also contains a check box labeled **Gated**. When this check box is selected, a given row of the table looping grid is processed (that is, the associated **Table Extractor** functoids are called for that row) only if the value of the first column of that row evaluates to **True**.

## Remarks

This property is available only for the **Table Looping** functoid, and is not enabled when any other type of functoid is selected.

For more information about how this property is used with the **Table Looping** functoid, see [Table Looping and Table Extractor Functoids](https://msdn.microsoft.com/library/aa559310\(v=bts.80\)).

## See Also

[General Functoid Properties](general-functoid-properties.md)  
[Table Looping Functoid Reference](table-looping-functoid-reference.md)  
[Table Extractor Functoid Reference](table-extractor-functoid-reference.md)  
[Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab](configure-table-looping-functoid-dialog-box-table-looping-grid-tab.md)

