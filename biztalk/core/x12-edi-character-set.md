---
title: "X12 EDI Character Set | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76e7b327-b0bd-4f16-8bfe-6c0184059f2b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# X12 EDI Character Set
When using the Ñ character or a grave accent (`), specify the following:  


|                                                                   |                                  Character Set                                   |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
|             Only the Ñ character in the EDI document              |                            Use Extended Character Set                            |
|           Only a grave accent (\`) in the EDI document            |                              Use UTF8 Character Set                              |
| The Ñ character **and** a grave accent (\`) in the same document: | -   The inbound document must have UTF8 encoding<br />-   Use UTF8 Character Set |

 The following links provider more information on EDI Character Sets:  

 [EDI Character Sets](http://go.microsoft.com/fwlink/p/?LinkId=271249)  

 [EDI Character Set Support](http://go.microsoft.com/fwlink/p/?LinkId=271250)