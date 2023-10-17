---
description: "Learn more about: X12 EDI Character Set"
title: "X12 EDI Character Set"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# X12 EDI Character Set

When using the Ñ character or a grave accent (`), specify the following:

| Character or grave access |  Character Set  |
|---|---|
| Only the Ñ character in the EDI document  |  Use Extended Character Set  |
|  Only a grave accent (\`) in the EDI document  |  Use UTF8 Character Set |
| The Ñ character **and** a grave accent (\`) in the same document: | -   The inbound document must have UTF8 encoding<br />-   Use UTF8 Character Set |

 The following links provider more information on EDI Character Sets:

 [EDI Character Sets](edi-character-sets.md)

 [EDI Character Set Support](edi-character-set-support.md)
