---
description: "Learn more about: How to Terminate a Connection with Session Integrator for LU2"
title: "Terminate a Connection with Session Integrator for LU22"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Terminate a Connection with Session Integrator for LU2
After you have finished sending and receiving information on your LU2 connection, you must shut your connection down with a call to `Microsoft.HostIntegration.SNA.Session.SessionDisplay.Disconnect%2A`.  
  
## Shut an LU2 connection down  
  
1.  When you are finished with your connection, call `SessionDisplay.Disconnect` to disconnect.  
  
## Example  
 The following code example is from the 3270 application in the Host Integration Server SDK.  
  
```  
private void Disconnect_Click(object sender, EventArgs e)  
        {  
            // Disable every button and text box.  
            DisableEverything();  
  
            m_Handler.Disconnect();  
  
            // Go back to the original state of buttons.  
            SetOpeningState();  
        }  
```  
  
## See Also  
 [Session Integrator for LU2](../core/session-integrator-for-lu21.md)
