---
title: Output Instance Filename (Schema File Property)
TOCTitle: Output Instance Filename (Schema File Property)
ms:assetid: 17a77178-8e84-41bd-a2a2-6ee5d8f0e409
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558782(v=BTS.80)
ms:contentKeyID: 51526449
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Output Instance Filename (Schema File Property)

 

Use the **Output Instance Filename** property to configure the full path of the file to which to which generated instance messages will be written.

## Category

General

## Allowed Values

Valid, full path file names.

## Default Value

None.

## Remarks

You can examine and set this property in the **Property Pages** dialog box that is displayed when you right-click a schema file in Visual Studio Solution Explorer and then click **Properties** on the shortcut menu.

You can provide this property value in several ways:

  - Type or paste the full path of the file to contain the output instance message into the edit box.

  - Browse to locate the file to contain the output instance message by clicking the ellipsis (**...**) button located to the right of the edit box to open the **Select Output File** dialog box.

If you do not provide a value for this property, generated output instance messages will be written to your designated temporary folder using a path and filename of the following form:

```C#
C:\Documents and Settings\<UserName>\Local Settings\Temp\_SchemaData\<SchemaName>_output.<xml|txt>  
```

## See Also

[Schema File Properties](schema-file-properties.md)  
[Generate Instance Output Type (Schema File Property)](generate-instance-output-type-schema-file-property.md)

