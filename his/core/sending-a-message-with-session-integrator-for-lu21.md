---
title: "Sending a Message with Session Integrator for LU21 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fdae53c-ad33-4cf1-a20a-f34c44ffc18a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending a Message with Session Integrator for LU2
After you create a connection, you can send information over the LU2 connection to the remote display.  
  
### To send a message using Transaction Integrator for LU2  
  
1.  If necessary, move the cursor to the position that you want to write to on the screen by calling one of the `SessionDisplay.Move` methods.  
  
     <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay> contains a variety of <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay.MoveCursor%2A>, <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay.MoveNextField%2A>, <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay.MovePreviousField%2A>, and <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay.MoveToField%2A> overloads. These overloads enable you to move the cursor to different parts of the screen, depending on what information you provide.  
  
     The `SessionDisplay.Move` methods are mirrored by a similar set of `SessionDisplay.Get` methods, which enable you to retrieve the location of the cursor, as well as the information contained in different fields on the screen.  
  
2.  Send information to the current cursor position using a call to `SessionHandler.sendKey`.  
  
     `sendKey` sends a specified string to the location on the screen marked by the cursor. If no cursor location is available, `sendKey` sends the information to the default location.  
  
## Example  
 The following code is from the 3270 application in the SDK sample directory. In this sample, the developer assumes that the cursor is in the default location on the screen, and therefore does not confirm the cursor location.  
  
```  
private void ConnectCICS_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                CICSName.Text = CICSName.Text.Trim();  
                if (CICSName.Text.Length == 0)  
                {  
                    MessageBox.Show("You must fill out the CICS Name");  
                    return;  
                }  
                // Disable every button and text box.  
                DisableEverything();  
                m_Handler.SendKey(CICSName.Text + "@E");  
                TraceScreen();  
                m_Handler.WaitForSession (SessionDisplayWaitType.PLUSLU, 5000);  
                TraceScreen();  
                m_Handler.WaitForContent(@"DEMONSTRATION", 20000);  
                TraceScreen();  
                // Enable clear screen.  
                EnableClearScreen();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
  
```  
  
## See Also  
 <xref:Microsoft.HostIntegration.SNA.Session.SessionDisplay>   
 [Session Integrator for LU2](../core/session-integrator-for-lu21.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu02.md)