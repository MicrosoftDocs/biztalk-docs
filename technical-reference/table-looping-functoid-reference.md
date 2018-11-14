---
title: Table Looping Functoid Reference
TOCTitle: Table Looping Functoid Reference
ms:assetid: 1f284a8a-3cfb-4397-b9a9-aa6315919716
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559129(v=BTS.80)
ms:contentKeyID: 51526707
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Table Looping Functoid Reference

 

Use the **Table Looping** functoid ( ![](images/Aa559129.8f4b3620-4778-4d73-a60d-b11dea1766aa(BTS.80).jpeg)), in conjunction with one or more **Table Extractor** functoids, to create a repeating structure in an output instance message by using constant values, values from an instance message, and values that are output from other functoids. The Table Looping functoid can also be used to add records to the output structure when there is no input record. For more information, please refer to the [Table-Driven Looping Example](https://msdn.microsoft.com/library/aa578676\(v=bts.80\)).

## Input

**Parameter 1:** A link from a repeating node in the source schema. The number of instances of this structure that occur in a particular input instance message defines the number of times that the associated table looping grid is processed.

**Parameter 2:** A constant input parameter that defines the number of columns in the associated table looping grid.

**Parameters 3 – 100:** A link from a node in the source schema or from another functoid, such as a [Value Extractor](value-extractor-functoid.md) functoid, or a constant input parameter. The relative order of parameters 3 – 100 is unimportant.

## Output

**Output 1:** A link to a repeating node in the destination schema, identifying the location of the repeating structure in output instance messages that is constructed by using values configured in the associated table looping grid.

**Outputs 2 – N:** One or more links to the associated **Table Extractor** functoids, one per such functoid.

## Remarks

You must use this functoid in conjunction with one or more **Table Extractor** functoids.

This functoid accepts multiple inputs, such as links from the source schema, constants, and the output of other functoids. You use these inputs to configure the table looping grid from which the associated **Table Extractor** functoids extract the data used to build the relevant portion of the output instance message You configure the table looping grid by using the [Configure Table Looping Functoid Dialog Box, Table Looping Grid Tab](configure-table-looping-functoid-dialog-box-table-looping-grid-tab.md). You access this dialog box by using the [Table Looping Grid (Functoid Property)](table-looping-grid-functoid-property.md). The Table Looping Grid is a property of **Table Looping** functoids.

Every cell in the table looping grid is a drop-down list that is populated by input parameters 3 through 100. How the entries in the drop-down list are represented depends on the type of the corresponding input parameter and, where applicable, on whether the [Label](label-link-property.md) property of the link is assigned a value. There are three possibilities:

1.  Constant input parameters are displayed as their values.

2.  Input parameters that are links from nodes in the source schema and for which no **Label** link property value is supplied are displayed by using the value of their [Link Source](link-source-link-property.md) functoid property.

3.  Input parameters that are links from another functoid and for which no **Label** link property value is supplied are displayed by using the value of their [(Name)](name-functoid-property.md) property.

In the case of 2 and 3 above, and especially in the case of 2, where the input parameters are links from nodes in the source schema, the effort involved in providing descriptive values for the **Label** property of the relevant link is generally well spent when the time comes to configure the table looping grid.

The **Table Looping Configuration** dialog box also has a check box with the label **Gated**. When you select this check box, you are specifying that the value of the data specified for column 1 controls whether any processing is performed for that row. When this is output from a logical functoid, if the value specified in column 1 evaluates to **False**, the associated row of the grid is skipped (meaning that the associated **Table Extractor** functoids are not invoked for that row). When column 1 is a field, then the functoid treats the presence of data as **True**; it treats the absence of data as **False**.


> [!NOTE]
> <P>The Table Looping functoid should not be used with the Value Mapping (Flattening) functoid. If both are used together, it results in a compiled map that assumed there is no source looping dependency for the target nodes that are below the <STRONG>Table Looping</STRONG> functoid.</P>



## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))  
[Table Looping and Table Extractor Functoids](https://msdn.microsoft.com/library/aa559310\(v=bts.80\))  
[How to Add Table Looping and Table Extractor Functoids to a Map](https://msdn.microsoft.com/library/aa559694\(v=bts.80\))

