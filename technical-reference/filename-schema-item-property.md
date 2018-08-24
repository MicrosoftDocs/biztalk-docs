---
title: Filename (Schema Item Property)
TOCTitle: Filename (Schema Item Property)
ms:assetid: f2185094-4476-4b4e-8ba5-7d5f4e9a797e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561884(v=BTS.80)
ms:contentKeyID: 51533348
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Filename (Schema Item Property)

 

Use the **Filename** property to examine and set the name of the selected schema file.

## Category

Miscellaneous

## Allowed Values

A valid, pathless file name with an .xsd extension.

## Default Value

Schema*N*.xsd, where "*N*" is a monotonically increasing number.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a schema file in Solution Explorer.

This property stores the actual name of the schema file on your hard disk. If you change this property value within the context of the project, the file is renamed on the disk and the project will be updated to reference the renamed file.

