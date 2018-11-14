---
title: Assert Functoid Reference
TOCTitle: Assert Functoid Reference
ms:assetid: 6fa11fc8-1fd2-403e-a961-f67714781aa6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560747(v=BTS.80)
ms:contentKeyID: 51528839
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Assert Functoid Reference

 

The **Assert** functoid (![Assert functoid](images/Aa560747.313715e0-e73d-4806-941a-413d5ad1dee3(BTS.80).jpeg "Assert functoid")) enables you to test your assumptions about conditions in your map. For example, if you perform some calculations to determine an additional discount on product purchases, you might assert that the additional discount be no more than $100 by using a logical functoid (**Greater Than** or **Less Than**).

## Input

**Parameter 1:** A Boolean value, generally from the output of some other **Logical** functoid or from a variable Boolean field in the input instance message.

**Parameter 2:** Text to use when throwing an exception if Parameter 1 is **False**. This should be a descriptive statement that can be used to locate the source of the failed assertion.

**Parameter 3:** Text to return if the Parameter 1 is **True**.

## Output

**Output 1:** The text value of **Parameter 3** if Parameter 1 is **True**; otherwise, the functoid throws an exception.

## Remarks

The **Assert** functoid only fires in development builds or when the **Generate Debugging Information**property in the project build settings is set to **True**. When your BizTalk Server application is compiled for deployment and the **Generate Debugging Information** property is set to **False** (the default), assertions are ignored.


> [!NOTE]
> <P>Balance the need for <STRONG>Assert</STRONG> functoid processing in production builds with the additional overhead that may be required to process them.</P>



## See Also

[Advanced Functoids Reference](advanced-functoids-reference.md)  
[Advanced Functoids](https://msdn.microsoft.com/library/aa561121\(v=bts.80\))

