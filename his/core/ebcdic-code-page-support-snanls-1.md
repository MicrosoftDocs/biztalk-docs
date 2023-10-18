---
description: "Learn more about: EBCDIC Code Page Support (SNANLS)"
title: "EBCDIC Code Page Support (SNANLS)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# EBCDIC Code Page Support (SNANLS)
The following table shows the EBCDIC code pages and character code set identifiers (CCSIDs) supported by SNA National Language Support (SNANLS) in Host Integration Server.  
  
|SNANLS Display Name|NLS Code Page|Host CCSID|euro|Supported by SNANLS|  
|-------------------------|-------------------|----------------|----------|-------------------------|  
|EBCDIC - Arabic|20420|420||partial (See Note)|  
|EBCDIC - Cyrillic (Russian)|20880|880||yes|  
|EBCDIC - Cyrillic (Serbian, Bulgarian)|21025|1025||yes|  
|EBCDIC - Denmark/ Norway (Euro)|1142|277|yes|yes|  
|EBCDIC - Denmark/ Norway|20277|277||yes|  
|EBCDIC - Finland/ Sweden (Euro)|1143|278|yes|yes|  
|EBCDIC - Finland/ Sweden|20278|278||yes|  
|EBCDIC - France (Euro)|1147|297|yes|yes|  
|EBCDIC - France|20297|297||yes|  
|EBCDIC - Germany (Euro)|1141|273|yes|yes|  
|EBCDIC - Germany|20273|273||yes|  
|EBCDIC - Greek (Modern)|875|875||yes|  
|EBCDIC - Greek|20423|423||yes|  
|EBCDIC - Hebrew|20424|424||partial (See Note)|  
|EBCDIC - Icelandic (Euro)|1149|871|yes|yes|  
|EBCDIC - Icelandic|20871|871||yes|  
|EBCDIC - International (Euro)|1148|500|yes|yes|  
|EBCDIC - International|500|500||yes|  
|EBCDIC - Italy (Euro)|1144|280|yes|yes|  
|EBCDIC - Italy|20280|280||yes|  
|EBCDIC - Japan English (Extended)|1027||||  
|EBCDIC - Japan English/Kanji (Extended)|939|939||yes|  
|EBCDIC - Japan English/Kanji (Extended)|5035||||  
|EBCDIC - Japan Katakana (Extended)|290|290||yes|  
|EBCDIC - Japan Katakana/Kanji (Extend Katakana)|930|930||yes|  
|EBCDIC - Japan Katakana/Kanji (Extend Katakana)|5026||||  
|EBCDIC - Japanese|931|931||yes|  
|EBCDIC - Korea (Extended)|933|933||yes|  
|EBCDIC - Latin America/<br /><br /> Spain (Euro)|1145|284|yes|yes|  
|EBCDIC - Latin America/<br /><br /> Spain|20284|284||yes|  
|EBCDIC - Multilingual/ ROECE (Latin-2)|870|870||yes|  
|EBCDIC - Simplified Chinese (Extended)|935|935||yes|  
|EBCDIC - Thai|20838|838||yes|  
|EBCDIC - Traditional Chinese (Extended)|937|937||yes|  
|EBCDIC - Turkish (Latin-3)|20905|905||yes|  
|EBCDIC - Turkish (Latin-5)|1026|1026||yes|  
|EBCDIC - U.S./ Canada (Euro)|1140|37|yes|yes|  
|EBCDIC - U.S./ Canada|37|37||yes|  
|EBCDIC - United Kingdom (Euro)|1146|285|yes|yes|  
|EBCDIC - United Kingdom|20285|285||yes|  
  
> [!NOTE]
>  Support for Arabic and Hebrew code page conversions are limited to left-to-right output. Bidirectional output including the default Arabic and Hebrew right-to-left output is not supported in this release of Host Integration Server.
