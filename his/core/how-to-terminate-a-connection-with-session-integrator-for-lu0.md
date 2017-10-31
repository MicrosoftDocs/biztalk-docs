---
title: "How to Terminate a Connection with Session Integrator for LU02 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 512a6db7-f025-4bcf-bdcd-28c2182a4920
caps.latest.revision: 3
---
# How to Terminate a Connection with Session Integrator for LU0
After you finish sending and receiving information over the LU0 session, you must terminate your connection. Ending a session with Session Integrator consists primarily of calling `SessionLU0.Disconnect`.  
  
### To terminate a connection with Session Integrator for LU0  
  
1.  End the connection by using `SessionLU0.Disconnect`.  
  
     After you call `Disconnect`, you must call `Connect` in order to re-establish a connection. This is true even if the call fails to complete successfully.  
  
2.  If necessary, ensure that you have released all relevant data objects.  
  
## Example  
 The following code example shows how to terminate a Session Integrator session for LU0.  
  
```  
private void Disconnect_Click(object sender, EventArgs e)  
 {  
 // Disable every button and text box.  
  DisableEverything();  
  _session.Disconnect();  
// Go back to the original state of buttons.  
  SetOpeningState();  
  }  
```  
  
## See Also  
 [Session Integrator for LU0](../core/session-integrator-for-lu0.md)