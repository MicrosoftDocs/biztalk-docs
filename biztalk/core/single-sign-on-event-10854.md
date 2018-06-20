---
title: "Single Sign-On: Event 10854 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8faed9d-5c7e-4b99-bcd9-ea5f670d5e72
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10854
## Details  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10854                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |               ENTSSO_E_INVALID_STRING_FORMAT               |
|  Message Text   |     The string format is incorrect for this function.      |
  
## Explanation  
 The string format is incorrect for this function.  
  
## User Action  
 Proper formatting for password strings is described below:  
  
 VT_BSTR type property  
  
 The delimiter is / (slash)  
  
 dc = default case (no operation - do nothing)  
  
 Example: dc/  
  
 (no change - 'Cat' to 'Cat')  
  
 uc = upper case  
  
 Example: uc/  
  
 (change password to upper case - 'Cat' to 'CAT')  
  
 lc = lower case  
  
 Example: lc/  
  
 (change password to lower case - 'Cat' to 'cat')  
  
 rc = remove chars - followed by count followed by chars  
  
 Example: rc/2/#@/  
  
 (remove the characters '#' and '@' from the password - 'C@t#' to 'Ct')  
  
 sc = substitute chars - followed by count followed by chars to replace followed by substitute chars  
  
 Example: sc/3/abc/def/  
  
 (remove the characters 'a', 'b' and 'c' from the password and replace with 'd', 'e' and 'f' respectively)  
  
 ('Cat' to 'Cdt')  
  
 ps = pad from start - followed by count (min password length) followed by single pad char  
  
 Example: ps/8/#/  
  
 (if the password is not at least 8 chars in length then pad from the start with the character '#' until there are 8 chars total)  
  
 ('Cat' to '#####Cat')  
  
 pe = pad from end - followed by count (min password length) followed by single pad char  
  
 Example: pe/10/$/  
  
 (if the password is not at least 10 chars in length then pad to the end with the character '$' until there are 10 chars total)  
  
 ('Cat' to 'Cat$$$$$$$')  
  
 tr = truncate - limit length of string - followed by count  
  
 Example: tr/11/  
  
 ('Cat123456789' to 'Cat12345678');  
  
 The tokens are processed in their order in the string.  
  
 Example:  
  
 uc/rc/1/&/sc/2/#$/--/ps/8/&/tr/32/