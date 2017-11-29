---
title: "How to Terminate a Connection with Session Integrator for LU22 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc795382-8952-441b-be79-e350e2f41ad2
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Terminate a Connection with Session Integrator for LU2
After you have finished sending and receiving information on your LU2 connection, you must shut your connection down with a call to <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay.Disconnect%2A>.  
  
### To shut an LU2 connection down  
  
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
 <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay>   
 [Session Integrator for LU2](../core/session-integrator-for-lu2.md)