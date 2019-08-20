---
title: "IBM DBCS Code Pages1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ceb7ef63-b25b-46a8-9c49-b905a828439f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# IBM DBCS Code Pages
Transaction Integrator (TI) recognizes the following code pages as IBM double-byte character set (DBCS) code pages:  
  
|Code page|Description|  
|---------------|-----------------|  
|930|IBM Extend Katakana and IBM Japanese (for Japan)|  
|931|IBM English lower case and IBM Japanese (for Japan)|  
|933|IBM Hungle Extend single-byte and IBM Hungle (for Korea)|  
|935|IBM English single-byte and IBM simplified Chinese (for PRC)|  
|937|IBM English single-byte and IBM traditional Chinese|  
|939|IBM English Extend lower case and IBM Japanese (for Japan)|  
  
 All other code pages delivered with Host Integration Server are handled as Extended Binary Coded Decimal Interchange Code (EBCDIC) code pages, which use a single byte to represent a character.  
  
 When the TI run-time environment converts UNICODE characters to DBCS characters, it uses standard Microsoft Windows NLS code pages.  
  
 The following table lists the DBCS code pages and their corresponding NLS code pages.  
  
|DBCS<br /><br /> code page|NLS code page required by TI|  
|------------------------|----------------------------------|  
|930|932 ANSI Japan|  
|931|932 ANSI Japan|  
|933|949 ANSI Korean|  
|935|936 ANSI Chinese (China, Singapore)|  
|937|950 ANSI Chinese|  
|939|932 ANSI Japan|  
  
 The list of code pages on the **Locale** property page for a remote environment includes a DBCS code page only if the corresponding NLS code page is loaded on the computer. The following code pages have been added for European support.  
  
|Code page|IBM or open systems name|Display name|  
|---------------|------------------------------|------------------|  
|923|ISO 8859-15 Latin 9 (Euro)|Latin-9 (Euro)|  
|924|IBM Latin - 1/Open System|Latin-1 Open System (Euro)|  
|858|OEM - Multilingual Latin 1 (Euro)|OEM - Multilingual Latin 1 (Euro)|  
|1140|IBM EBCDIC - U.S./Canada (Euro)|U.S./Canada (Euro)|  
|1141|IBM EBCDIC - Germany (Euro)|Germany (Euro)|  
|1142|IBM EBCDIC - Denmark/Norway (Euro)|Denmark/Norway (Euro)|  
  
## See Also  
 [Mainframe Character Strings and Code Pages](../core/mainframe-character-strings-and-code-pages2.md)