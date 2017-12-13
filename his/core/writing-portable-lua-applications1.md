---
title: "Writing Portable LUA Applications1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0ee110a-95e2-4821-8f9a-efc3b8039c68
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Writing Portable LUA Applications
Use the following guidelines for writing logical unit application (LUA) applications that are portable to other environments:  
  
-   Use the symbolic constant names for parameter values and return codes, and not the numeric values shown in the WINLUA.H file. (For more information, see the WINLUA.H file in the Microsoft® Host Integration Server SDK.)  
  
-   When accessing SNAsense codes in a data buffer, use the symbolic constants rather than the numeric values. This ensures that the byte storage order is correct for your particular system. You should use **memcpy** to set the values, and **memcmp** to test them. For example:  
  
    ```  
    memcpy (this_verb.common.lua_data_ptr, LUA_INCORRECT_REQ_CODE, 4);  
    if (memcmp (this_verb.common.lua_data_ptr,  
    LUA_INCORRECT_REQ_CODE, 4) == 0)  
    {  
    .....  
    }  
    ```  
  
-   Ensure that any parameters shown as reserved are set to zero.  
  
-   Set the **lua_verb_length** parameter as described in the verb description.