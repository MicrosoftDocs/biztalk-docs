---
title: TestMap Input Instance (Map File Property)
TOCTitle: TestMap Input Instance (Map File Property)
ms:assetid: 403f5c2f-bc89-46a4-a309-4841172c4b45
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559765(v=BTS.80)
ms:contentKeyID: 51527523
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# TestMap Input Instance (Map File Property)

 

Use the **TestMap Input Instance** property to configure the location of the input instance message file to be used to test the map.

## Category

Test Map

## Allowed Values

Valid name of a file that contains the instance message that you want to use when testing the map.

Either type the full path name of the file or use the ellipsis (**...**) button on the right side of the input field to open the **Select Input File** dialog box.

## Default Value

None.

## Remarks

Configure this property if you want to test your map by using a custom instance message rather than an instance message generated automatically by BizTalk Mapper. For more information about automatic generation of input instance messages versus providing a custom input instance message, see [TestMap Input (Map File Property)](testmap-input-map-file-property.md).


> [!NOTE]
> <P>Remember to set the <STRONG>TestMap Input</STRONG> property to XML. Otherwise BizTalk will continue to generate an input instance message rather than using the file you specified.</P>



## See Also

[Map File Properties](map-file-properties.md)

