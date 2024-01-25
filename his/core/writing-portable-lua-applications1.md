---
description: "Learn more about: Writing Portable LUA Applications"
title: "Writing Portable LUA Applications1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
