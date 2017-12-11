---
title: "How to Terminate a Connection with Session Integrator for LU01 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89210007-eef2-480e-93e7-cb5027cd6bc2
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
 [Session Integrator for LU0](../HIS2010/session-integrator-for-lu01.md)