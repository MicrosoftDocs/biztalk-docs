---
title: "How the Designer Extensibility Sample Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f4dc622-28b8-498d-961f-df969cff9dcb
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the Designer Extensibility Sample Works
Each project in the Designer Extensibility sample contains two classes: an **Extender** class and an **Extension Provider** class. These classes are designed to extend the capabilities and define the properties of the **ItineraryDsl** model elements.  
  
 The **Extension Provider** classes derive from the **ExtensionProviderBase** class and have the **ExtensionProviderAttribute** applied to them with properties that identify the extension and its purpose. These values will be displayed to the user in the designer when the user is setting the **Extender** property on a model element. When the **Extension Provider** classes initialize, they call to the constructor for the **ExtensionProviderBase** and pass to it the type of the extender class.  
  
 The **Extender** classes have an **ObjectExtender** attribute applied to them; to the **ObjectExtender** attribute, they pass the type of the object in the **ItineraryDsl** that they extend. The base class for these classes varies, depending on the type of extender. For Resolver extenders, the base class is **ObjectExtender\<Resolver>**. For Itinerary Service extenders, the base class is **ItineraryServiceExtenderBase**. In the **Extender** classes, the following attributes are applied to the properties: attributes necessary for proper display in a property grid, attributes included in the Microsoft Enterprise Library for validation purposes, attributes necessary for proper serialization, and/or attributes that determine how properties are persisted.  
  
 When these assemblies are compiled and placed in the Lib folder, they are loaded and cached by the designer at run time. As extenders are needed, the **ItineraryDsl** uses reflection to load the applicable assemblies from the cache by examining the types exported and the attributes on those types.