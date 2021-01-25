---
description: "Learn more about: Input Parameters (Functoid Property)"
title: Input Parameters (Functoid Property)
TOCTitle: Input Parameters (Functoid Property)
ms:assetid: e7af7273-1d80-4c6e-bb3e-0091700d35db
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561660(v=BTS.80)
ms:contentKeyID: 51533058
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Input Parameters (Functoid Property)

 

Use the **Input Parameters** property to open the **Configure \<Functoid\> Functoid** dialog box, in which you can configure input parameters for the functoid, including changing the order of the input parameters when necessary, and creating constant input parameters to supplement the link input parameters.

## Category

General

## Value

The value of this property is an ordered list of input parameters for the selected functoid. These input parameters are of two types:

  - **Link input parameters.** Link input parameters are the set of links attached to the left side of the selected functoid in a grid page, if any. These input parameters are created by dragging between the selected functoid and either a node in the source schema or another functoid located to the left of the selected functoid in the same grid page. Link input parameters that have been given a **Label** property value are shown in the input parameters list using that value; otherwise, the value of the **Link Source** property is shown (generally, the former is friendlier than the latter).

  - **Constant input parameters.** Constant input parameters are constant values that are created within the **Configure \<Functoid\> Functoid** dialog box by using the **Insert New Constant Input Parameter** button
    
    ![Adding constant input parameters to a functoid](images/Aa561660.e2c2e13d-f9ec-45e9-9f75-02a0d51b8941(BTS.80).jpeg "Adding constant input parameters to a functoid")
    
    . Clicking this button inserts a new constant input parameter and provides an in-place edit box in which you can type its value. Thereafter, it is shown in the input parameters list using this value.

The order of input parameters is important to proper functoid operation, and you must use the **Configure \<Functoid\> Functoid** dialog box to examine and change this order when necessary. Link input parameters are initially ordered by the order in which they are created, and constant input parameters are initially added to the end of the input parameter list. Use the **Move Selected Input Parameter Up**![Move up in the list](images/Aa561660.bb10da30-7479-46c9-87c1-9e8f6acbd4cc(BTS.80).jpeg "Move up in the list") and the Move Selected Input Parameter Down ![Moving down in a list](images/Aa561660.d15466eb-309d-449a-969c-1659d5164e58(BTS.80).jpeg "Moving down in a list") buttons to change the order of the input parameters. For information about the proper order of input parameters to the various functoids, see [Functoid Reference](functoid-reference.md).

## Remarks

To undo a set of changes made in this dialog box, click **Cancel** to close the dialog box without saving changes, and then reopen it.

For more information about how this property is used to establish the correct set of input parameters to a functoid, see [Editing Functoid Properties and Input Parameters](https://msdn.microsoft.com/library/aa559242\(v=bts.80\)).

## See Also

[General Functoid Properties](general-functoid-properties.md)

