---
title: "Issuing an LUA Verb1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8aaf92e-2851-43ce-8bf6-938eefa3b686
caps.latest.revision: 3
---
# Issuing an LUA Verb
The following procedure is required to issue a logical unit application (LUA) verb. In this example, the verb issued is [RUI_INIT](../core/rui-init2.md).  
  
### To issue an LUA verb  
  
1.  Create a variable for the verb control block (VCB) structure. For example:  
  
    ```  
    #include <winlua.h>  
            .  
            .  
    struct LUA_VERB_RECORD rui_init;  
  
    ```  
  
2.  The [LUA_VERB_RECORD](../core/lua-verb-record1.md) structure is declared in the WINLUA.H header file.  
  
3.  Clear (set to zero) the variables within the VCB:  
  
    ```  
    memset( &rui_init, 0, sizeof( rui_init) );  
    ```  
  
     LUA requires that all reserved parameters, and all parameters not required by the verb being issued, must be set to zero. The simplest way to do this is to set the entire VCB to zeros before setting the parameters required for this particular verb.  
  
4.  Assign values to the VCB parameters that supply information to LUA:  
  
    ```  
    rui_init.common.lua_verb = LUA_VERB_RUI;  
    rui_init.common.lua_verb_length = sizeof(struct LUA_COMMON);  
    rui_init.common.lua_opcode = LUA_OPCODE_RUI_INIT;  
    memcpy (rui_init.common.lua_luname, "THISLU  ", 8);  
    ```  
  
     The values LUA_VERB_RUI and LUA_OPCODE_RUI_INIT are symbolic constants. These constants are defined in the WINLUA.H header file in the Host Integration Server SDK. To ensure portability between different systems, use symbolic constants and not integer values.  
  
5.  Invoke LUA. The only parameter is a pointer to the address of the structure containing the VCB for the desired verb.  
  
    ```  
    RUI( &rui_init );  
    ```  
  
6.  Check the asynchronous flag (**rui_init.common.lua_flag2.async**) to determine whether the verb completed asynchronously. If events are being used and the verb did complete asynchronously, wait for the event to complete.  
  
    ```  
    if (rui_init.common.lua_flag2.async)  
    {  
    /* verb will complete asynchronously so continue  
    with other processing */  
    /* then wait */  
    WaitForSingleObject (...)  
    }  
    ```  
  
     Do not check the return code. It may have changed from LUA_IN_PROGRESS to LUA_OK by the time you check it.  
  
7.  Check the variables returned by LUA.  
  
    ```  
    if( rui_init.common.lua_prim_rc == LUA_OK )  
    {  
    /* Init OK */  
            .  
            .  
    }   
    else  
    {  
    /* Do error routine */  
            .  
            .  
    }  
    ```