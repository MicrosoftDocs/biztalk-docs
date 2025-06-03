---
description: "Learn more about: How to Terminate a Connection with Session Integrator for LU0"
title: "How to Terminate a Connection with Session Integrator for LU02"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
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
 [Session Integrator for LU0](../core/session-integrator-for-lu02.md)
