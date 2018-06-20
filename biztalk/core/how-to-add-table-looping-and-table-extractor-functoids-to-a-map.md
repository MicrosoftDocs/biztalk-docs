---
title: "How to Add Table Looping and Table Extractor Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c837ab8-55db-471a-af26-9fbd0497d7d4
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Table Looping and Table Extractor Functoids to a Map
The **Table Looping** and **Table Extractor** functoids are used together. The **Table Looping** functoid has an internal table you configure. For each input record or field, the **Table Looping** functoid outputs the rows of the table, one at a time. The **Table Extractor** functoid extracts the desired item from a row and passes it on to the output instance message.  
  
 For conceptual information about the **Table Looping** and **Table Extractor** functoids, see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md).  
  
### To add the Table Looping and Table Extractor functoids to a map and configure them  
  
1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.  
  
    The list of advanced functoids in the chosen category appears.  
  
2. Drag the **Table Looping** functoid (![](../core/media/advtablelooping.gif "advtablelooping")) from the Toolbox to the appropriate location on a grid page.  
  
   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that grid page first.  
  
   > [!NOTE]
   >  Because the output of the **Table Looping** functoid serves as input to one or more associated **Table Extractor** functoids, make sure you leave room to the right of the **Table Looping** functoid for the **Table Extractor** functoids.  
  
3. Drag a record or field from the source schema to the newly added **Table Looping** functoid. As the first input parameter to the **Table Looping** functoid, the number of occurrences of this record or field in an instance message will control the number of times this functoid produces output. For example, if a looping record is dragged to the functoid, and an instance message that has 10 occurrences of this record is processed, and the table grid has been configured with one row of sources of column data, the **Table Looping** functoid will iterate 10 times, producing 10 output rows for extraction by a **Table Extractor** functoid, and allowing 10 destination records to be easily constructed.  
  
   > [!NOTE]
   >  If you configure multiple rows in the table grid, each such row will be output for each iteration of the **Table Looping** functoid. So, the number of occurrences of an input record times the number of rows configured in the table grid yields the number of output table rows available for data extraction.  
  
4. Drag a record or field from the destination schema to the **Table Looping** functoid. This link ensures the creation of the node in the destination schema.  
  
5. Select the newly added **Table Looping** functoid, and in the **Properties** window, click the ellipsis (**...**) button associated with its **Input Parameters** property.  
  
   > [!NOTE]
   >  Alternatively, you can select the functoid and then press CTRL+M, CTRL+T from the keyboard. For a list of Mapper keyboard shortcuts see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
6. In the **Configure Table Looping Functoid** dialog box, click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button to create the second input parameter. Type a number that represents the number of columns that will be available in the table you are creating for this **Table Looping** functoid.  
  
   > [!NOTE]
   >  The maximum number of columns in the table is 228.  
  
7. In the **Configure Table Looping Functoid** dialog box, click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button to enter any constant values that appears in your configured table grid. The order in which you create these constants is not important in this dialog box as long as the first and second parameter values, the number of rows and columns, respectively, retain their positions at the beginning of the input parameter list. When complete, click **OK**.  
  
    The **Configure Table Looping Functoid** dialog box closes.  
  
8. Drag zero or more record or field nodes from the source schema to the **Table Looping** functoid that you recently added. Each of these record and field nodes is added to the end of the input parameter list, and therefore will be available when the table grid is configured in a latter step. Like the table data constants added earlier (not the row and column count constants), the order in which these record and field nodes are added is not ultimately relevant.  
  
9. To label a link, follow these steps:  
  
   - Select a link in the displayed grid page.  
  
   - In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, provide a descriptive name for the **Label** property. For example, you might give a name like "link2ndAuthor" to a link coming from a field called "Second Author".  
  
10. Select the newly added **Table Looping** functoid, and in the **Properties** window, click the ellipsis (**...**) button associated with the **Table Looping Grid** property associated with that functoid.  
  
     The **Configure Table Looping Functoid** dialog box appears with the **Table Looping Grid** tab selected.  
  
    > [!NOTE]
    >  Alternatively, you can right-click the functoid, and then click **Configure Table Looping Grid** in the context menu. The **Configure Table Looping Functoid** dialog box appears with the **Table Looping Grid** tab selected.  
  
11. Use the drop-down lists associated with each table cell to configure at least one, and possibly multiple, rows in the grid. The choices available in the drop-down lists are the constants and links that you have configured in steps 6-8 as input parameters 3 and up to the **Table Looping** functoid. (Input parameters 1 and 2 do not appear in these drop-down lists.) When complete, click **OK**.  
  
     The **Configure Table Looping Functoid** dialog box closes.  
  
    > [!NOTE]
    >  Each row constitutes one iteration of the output structure, in combination with the number of occurrences of the record or field specified as the first input parameter of the **Table Looping** functoid. For more information, see step 3.  
  
    > [!NOTE]
    >  You must select a value for each column you intend to access using a **Table Extractor** functoid. If a column is not used by a **Table Extractor** functoid, you should consider removing, rather than maintaining, that column.  
  
    > [!NOTE]
    >  The order of filling out the table grid is not important.  
  
12. Drag as many **Table Extractor** functoids (![](../core/media/advtableextractor.gif "advtableextractor")) from the Toolbox to the displayed grid page as needed.  
  
    > [!NOTE]
    >  Because the input of these **Table Extractor** functoids comes from the **Table Looping** functoid added in a previous step, make sure that you place the **Table Extractor** functoids to the right of the **Table Looping** functoid in the displayed grid page.  
  
13. To create the first input parameter for one of the **Table Extractor** functoids added in step 9, drag it to the relevant **Table Looping** functoid to its left.  
  
14. To create the second input parameter for the same **Table Extractor** functoid, select the functoid, and in the **Properties** window, click the ellipsis (**...**) button associated with its **Input parameters** property.  
  
     The **Configure Table Extractor Functoid** dialog box appears.  
  
15. Click the ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters") button to create the second input parameter. Type the number of the column in the table grid of the corresponding **Table Looping** functoid from which you want to extract data. Click **OK**.  
  
     The **Configure Table Extractor Functoid** dialog box closes.  
  
    > [!NOTE]
    >  Column numbers start at 1.  
  
16. To use the output of the **Table Extractor** functoid, drag the **Table Extractor**  functoid to a record or field node in the destination schema, or drag a record or field node in the destination schema to the **Table Extractor** functoid. The element or attribute value in a destination instance message corresponding to this record or field node in the destination schema will be populated with the value from (in the case of constants), or the value indicated by (in the case of links), the specified cell in the table grid.  
  
17. Repeat steps 12, 13, 14, and 15 for each of the **Table Extractor** functoids added in step 11.  
  
## See Also  
 [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)