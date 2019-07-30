---
title: "Receive Messages with Session Integrator for LU2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d77ce2b-348f-4cc5-a57d-60973f76c49f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Receiving Messages with Session Integrator for LU2
After you create an LU2 session, you can retrieve information and messages from the 3270 console through the `Microsoft.HostIntegration.SNA.Session.ScreenData` and `Microsoft.HostIntegration.SNA.Session.SessionDisplay` objects.  
  
## Receive information over an LU2 connection  
  
1.  If necessary, retrieve the entire screen as a screen dump using `Microsoft.HostIntegration.SNA.Session.ScreenData`.  
  
     For most circumstances, retrieving all the information on the screen is not necessary. Instead, you can use the `Microsoft.HostIntegration.SNA.Session.SessionDisplay` object for most applications.  
  
2.  Get the location of the cursor with a call to `Microsoft.HostIntegration.SNA.Session.ScreenCursor`.  
  
3.  Optionally, you can get the location and information contained within different fields on the screen with a call to one of the `Microsoft.HostIntegration.SNA.Session.SessionDisplay.GetField%2A` or `Microsoft.HostIntegration.SNA.Session.SessionDisplay.GetFields%2A` methods, or the `Microsoft.HostIntegration.SNA.Session.SessionDisplay.CurrentField%2A` property.  
  
     `Microsoft.HostIntegration.SNA.Session.SessionDisplay.GetField%2A` and `Microsoft.HostIntegration.SNA.Session.SessionDisplay.GetFields%2A` both contain multiple overloads, allowing you to retrieve field information from the screen, depending on what information you provide. In contrast, `Microsoft.HostIntegration.SNA.Session.SessionDisplay.CurrentField%2A` represents only the field the cursor is currently in.  
  
4.  Finally, you can receive field update information with a call to the various `SessionDisplay.Wait` methods.  
  
## Example  
 The following code is from the 3270 application in the Host Integration Server SDK. The sample uses `SessionDisplay.CurrentField.Data` to access the screen data.  
  
```  
private void PerformTX_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                // Disable every button and text box.  
                DisableEverything();  
  
                m_Handler.SendKey("@E");  
                TraceScreen();  
  
                // Wait for screen to calm down.  
                m_Handler.WaitForSession(SessionDisplayWaitType.NotBusy, 5000);  
                TraceScreen();  
  
                // See if the Balance Field is filled out.  
                m_Handler.Cursor.Row = m_row;  
                m_Handler.Cursor.Column = m_column;  
                TraceScreen();  
                // Tab to the Account Number field.  
                m_Handler.SendKey("@T");  
                TraceScreen();  
                // Move to the Next Field (Empty Stuff after 123456).  
                m_Handler.MoveNextField();  
                TraceScreen();  
                // Move to the Next Field (Title, Account Balance).  
                m_Handler.MoveNextField();  
                TraceScreen();  
                // Move to the Next Field (Account Balance).  
                m_Handler.MoveNextField();  
                TraceScreen();  
  
                // Extract Data from this field.  
                string accountBalance = m_Handler.CurrentField.Data;  
  
                // Trim the string.  
                accountBalance = accountBalance.Trim();  
  
                // Only things to do now are clear screen or disconnect.  
                EnableClearScreen();  
  
                // If we failed (not Abended) then this field will be blank.  
                if (accountBalance.Length == 0)  
                    throw new Exception("Failed to get Account Balance");  
                else  
                    MessageBox.Show(accountBalance, "Account Balance");  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
```  
  
## See Also  
 [Session Integrator for LU2](../core/session-integrator-for-lu21.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu02.md)