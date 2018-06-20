---
title: "How to Assign a Different Code Page to a Remote Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae52a594-18c9-4dc5-acb4-43b80942aa05
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Assign a Different Code Page to a Remote Environment
Use a remote environment (RE) to describe each CICS or IMS mainframe environment. Use Transaction Integrator (TI) Manager to create, modify, and delete REs.  
  
 Every RE description includes a property value for the code page that is to be used by the TI run-time environment to convert characters to and from mainframe data representations.  
  
 When you create a new RE, TI Manager automatically selects a code page based on the current system locale. However, you can replace this default value with a code page that you select.  
  
 As needed, you can use TI Manager to assign a different code page to any RE.  
  
### To select a different code page for an RE  
  
1. On the **Start** menu, point to **Programs**, then **Microsoft Host Integration Server**, and then click **TI Manager**.  
  
2. Expand the **Remote Environments** node.  
  
3. Right-click the remote environment to be modified, and then click **Properties**.  
  
4. On the **Locale** tab, clear the check box **Use default code page for the selected locale**.  
  
5. On the **Locale** tab, select the new code page from the **Code page** dropdown list.  
  
   Only the code page value is significant to the TI run-time environment when it converts character data. Although you can use the locale displayed on the **Locale** property page to select the code page, the TI run-time environment ignores it and uses only the code page value that is associated with that locale.  
  
## See Also  
 [Mainframe Character Strings and Code Pages](../core/mainframe-character-strings-and-code-pages2.md)