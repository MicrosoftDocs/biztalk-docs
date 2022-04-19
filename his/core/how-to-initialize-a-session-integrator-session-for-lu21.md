---
description: "Learn more about: Initialize a Session Integrator Session for LU2"
title: "Initialize a Session Integrator Session for LU21 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1873c18-e4c2-4633-abbf-a5873ea8f90e
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Initialize a Session Integrator Session for LU2
The first action that you must perform when you are connecting to an LU2 session for Transaction Integrator is to create and initialize the `Microsoft.HostIntegration.SNA.Session.SessionDisplay` object. As the name implies, `Microsoft.HostIntegration.SNA.Session.SessionDisplay` represents the 3270 display to your application, and is the primary interface that you will use to access the SNA network.  
  
 After you initialize your connection, you can begin to send and receive information over your LU2 session.  
  
## Procedure Title  
  
1.  If necessary, create a new session connection with `Microsoft.HostIntegration.SNA.Session.SessionConnectionDisplay`.  
  
     You can create the `Microsoft.HostIntegration.SNA.Session.SessionConnectionDisplay` directly if you have all the relevant information. However, you do not need to perform this step. More likely, you will simply pass in the LU connection string in step 2.  
  
2.  Create a new session with `Microsoft.HostIntegration.SNA.Session.SessionDisplay`.  
  
3.  Pass the connection information to `Microsoft.HostIntegration.SNA.Session.SessionDisplay.Connect%2A`.  
  
     `Microsoft.HostIntegration.SNA.Session.SessionDisplay.Connect%2A` contains several overloads: you can choose to connect with an already-created `Microsoft.HostIntegration.SNA.Session.SessionDisplay` object, a `Microsoft.HostIntegration.SNA.Session.SessionDisplay` object and additional initialization information, or with a connection string and initialization information.  
  
     If you choose to call `Microsoft.HostIntegration.SNA.Session.SessionDisplay.Connect%2A` with a connection string, Transaction Integrator will create a new `Microsoft.HostIntegration.SNA.Session.SessionConnectionDisplay` for you. You can directly access the `Microsoft.HostIntegration.SNA.Session.SessionConnectionDisplay` object through `Microsoft.HostIntegration.SNA.Session.SessionDisplay.Connection%2A`.  
  
4.  If necessary, confirm that you connected using `Microsoft.HostIntegration.SNA.Session.SessionDisplay.IsConnected%2A`.  
  
## Example  
 The following code is from the COM3270 application in the SDK sample directory.  
  
```  
private void CreateSession_Click(object sender, EventArgs e)  
        {  
            try  
            {  
                LUName.Text = LUName.Text.Trim();  
                if (LUName.Text.Length == 0)  
                {  
                    MessageBox.Show("You must fill out the LU or Pool Name");  
                    return;  
                }  
                m_Handler = new SessionDisplay();                m_Handler.Connect("TRANSPORT=SNA;LOGICALUNITNAME=" + LUName.Text);  
                m_Handler.Connection.HostCodePage = 37;  
  
                FontFamily fontFamily = new FontFamily("Courier New");  
                m_FixedFont = new Font(fontFamily, 10, FontStyle.Regular, GraphicsUnit.Pixel);  
                ScreenText.Font = m_FixedFont;  
                TraceScreen();  
  
                // Disable every button and text box.  
                DisableEverything();  
  
                m_Handler.WaitForContent("TERM NAME", 20000);  
                TraceScreen();  
  
                // Enable Connect to CICS and Disconnect Session.  
                EnableCICSElements();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.Message);  
            }  
        }  
```  
  
## See Also  
 [Session Integrator for LU2 Code Example](../core/session-integrator-for-lu2-code-example2.md)   
 [Session Integrator for LU2](../core/session-integrator-for-lu21.md)
