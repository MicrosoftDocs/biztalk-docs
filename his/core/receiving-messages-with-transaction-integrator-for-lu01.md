---
description: "Learn more about: Receiving Messages with Transaction Integrator for LU0"
title: "Receiving Messages with Transaction Integrator for LU01 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f493a6ba-7cdb-475e-8554-8d1e0ac5ee77
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Receiving Messages with Transaction Integrator for LU0
After you create and initialize your connection, you can receive information from the specified logical unit (LU). The primary way of receiving information with Session Integrator is with the `SessionLU0.Receive` method.  
  
 After sending and receiving messages, you must disconnect from your Session Integrator session.  
  
## Receive information using Session Integrator for LU0  
  
1.  Use SessionLU0.Receive and `SessionLU0data` to wait for data from the LU.  
  
     `Receive` allows you to pass the maximum length of time to wait for information, as well as whether you want to send an automatic acknowledgement. `Receive` returns a `SessionLU0Data` object.  
  
## Example  
 The following code example demonstrates how to receive information with Session Integrator for LU0.  
  
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
    _session = new SessionLU0();    _session.Connect("LogicalUnitName=" + LUName.Text, SessionLU0InitType.SSCP);  
                // Receive the logon screen.  
    SessionLU0Data receivedData = _session.Receive(20000, true);                // Trace out the received data.  
    TraceData(false, receivedData.Data, receivedData.Indication);  
                // Disable every button and text box.  
    DisableEverything();  
                // Insert User/Password.  
    EnableInsertUserId();  
   }  
catch (Exception ex)  
 {  
  MessageBox.Show(ex.Message);  
 }  
}  
```  
  
 For more information about the code sample, see [Session Integrator for LU0 Code Example](../core/session-integrator-for-lu0-code-example2.md).  
  
## See Also  
 [How to Terminate a Connection with Session Integrator for LU0](../core/how-to-terminate-a-connection-with-session-integrator-for-lu02.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu02.md)   
 [Session Integrator for LU0 Code Example](../core/session-integrator-for-lu0-code-example2.md)   
 [IcomLU0 Interface](./icomlu0-interface2.md)
