---
title: "SWIFT Text | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SWIFT, text"
ms.assetid: 90851d38-7789-4b1b-813b-7943f77ab984
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SWIFT Text
The message text makes up the payload of the financial (FIN) message, and contains all of the data fields except the fields containing the sender, receiver, and message type. These three fields are contained in the header portion. Some messages also contain an optional User Header, which may also provide processing information.  
  
 Each FIN message payload consists of a series of fields in a defined sequence. These fields conform to the following rules:  
  
- The fields may be required or optional within the sequence.  
  
- A sequence may contain subsequences, and a subsequence may repeat within a sequence.  
  
- You can use a field in several message types.  
  
- Within a field, there may be elements or subfields. An element or subfield may be common to several fields.  
  
- Each repeating sequence is represented by a group node.  
  
- Each field may itself have multiple nodal levels, each described as a record.  
  
- A schema element represents only the lowest level subfield.  
  
- Common records and elements are defined in the common and base schema, as described below.  
  
- Some fields may be represented in several formats (such as party fields). Such fields are defined as choice fields in the schema.  
  
  Some fields have limited sets of values. For the most part, the schema lists these values. Schema definitions also include character set validation.