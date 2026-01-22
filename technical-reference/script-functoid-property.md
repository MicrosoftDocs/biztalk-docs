---
description: "Learn more about: Script (Functoid Property)"
title: Script (Functoid Property)
TOCTitle: Script (Functoid Property)
ms:assetid: 083334f8-2aa2-4054-9d11-6174b546156c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547082(v=BTS.80)
ms:contentKeyID: 51526036
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Script (Functoid Property)

 

Use the **Script** property to open the **Configure Functoid Script** dialog box, in which you can configure the custom script or compiled code to be associated with the corresponding **Scripting** functoid.

## Category

General

## Value

The value of this property is the collection of values configured in the **Configure Functoid Script** dialog box. This includes an appropriate combination of values for the following fields in that dialog box:

  - **Script Type.** Set to either **Inline C\#**, **External Assembly**, **Inline JScript .NET**, **Inline Visual Basic .NET**, **Inline XSLT**, or **Inline XSLT Call Template**.
    

    > [!IMPORTANT]
    > <P>When you switch from one inline language to another, any script you have written for the language you are switching from is not deleted. You must either delete that script manually, or make sure that your new language choice has a higher precedence than your old language choice by using the <A href="script-type-precedence-grid-property.md">Script Type Precedence</A> grid property.</P>



  - **Script Assembly.** Must be set when **Script Type** is set to **External Assembly**.

  - **Script Class.** Must be set when **Script Type** is set to **External Assembly**.

  - **Script Method.** Must be set when **Script Type** is set to **External Assembly**.

## Remarks

This property is only available for the **Scripting** functoid, and is not enabled when any other type of functoid is selected.

## See Also

[General Functoid Properties](general-functoid-properties.md)

