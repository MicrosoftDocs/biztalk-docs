---
description: "Learn more about: Namespace (Map Item Property)"
title: Namespace (Map Item Property)
TOCTitle: Namespace (Map Item Property)
ms:assetid: 177a6d92-4b6f-46f8-b7e6-605028234726
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558775(v=BTS.80)
ms:contentKeyID: 51526467
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Namespace (Map Item Property)

 

Use the **Namespace** property to specify an alternative .NET namespace for a map.

## Category

Advanced

## Allowed Values

Valid namespace identifiers can be entered as the value of this property.

## Default Value

The name of the BizTalk project in which the map was originally created.

## Remarks

If you change the value of this property, you must make sure that you change references to the selected map in any orchestrations that reference it.

To avoid compilation errors, you must make sure that the value of the [Fully Qualified Name](fully-qualified-name-map-item-property.md) property (created by concatenating the value of this property, a period (.) character, and the value of the [Type Name](type-name-map-item-property.md) property) is unique within the BizTalk project.

