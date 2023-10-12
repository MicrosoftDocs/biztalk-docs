---
description: "Learn more about: Effective Date Properties"
title: "Effective Date Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Effective Date Properties
PeopleSoft Enterprise provides the ability to schedule and keep track of planned items by using a special property called Effective Date (abbreviated EFFDT). Such items are either in effect or merely planned, depending on whether their date is before or after the PeopleSoft current date.  
  
 If the properties of a component interface contain such effective-dated items (that is, a field with a name of EFFDT), the adapter makes it possible for callers to retrieve the complete set of values or only those values not yet effective—those that can still be changed.  
  
## getHistoryItems Parameter  
 For component interfaces with properties that include an effective date, the adapter provides an additional parameter, called `getHistoryItems`, to the Get operations. This parameter is of type Boolean, and if it is set to True, all effective-dated items are returned. These include all past, current, and future effective-dated items.  
  
 If the `getHistoryItems` parameter is set to False, only the current and future effective-dated items are returned. Choose False if your intention is to add or change these items (because past items cannot be changed).  
  
 It is also possible to have multiple effective-dated items having the same effective date. In this situation, an additional property, Effective Sequence (EFFSEQ), must also be provided. The values of the EFFSEQ must be unique to differentiate items with the same effective date. See the PeopleSoft documentation for more information.  
  
## Modifying Past Effective-Dated Items  
 The `correctionMode` argument in both the [UpdateEx](../core/updateex-method.md) and [DeleteOnly](../core/deleteonly-method.md) methods control whether past effective dated items can be modified. If it is set to true, all items can be modified. Otherwise, modifying past effective dated item generates an exception.  
  
 When calling the deprecated `Update` method on a component interface that has effective-dated items, you must take care not to include any effective dates of a value earlier than the PeopleSoft current effective date, or the call fails with an exception. However, the current effective-dated item can be included as it is bypassed when setting properties. If Effective Sequence exists, then all current effective-dated items with matching Effective Sequences in the server are skipped when setting properties.  
  
## See Also  
 [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md)
