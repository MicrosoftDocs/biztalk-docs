---
title: "Sending a Message with Transaction Integrator for LU02 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ed407a0-cd0f-432a-9be4-64621e982ee7
caps.latest.revision: 3
---
# Sending a Message with Transaction Integrator for LU0
After you initialize and connect to the logical unit (LU), you can send information over the LU0 connection. The primary tool that Session Integrator exposes for sending LU0 information is the `SessionLU0Data` object and the `SessionLU0.Send` method.  
  
 In addition to sending information, you probably will want to receive information too.  
  
### To send a message using Transaction Integrator for LU0  
  
1.  Collect your data into the format your LU uses.  
  
2.  Place your data into a `SessionLU0Data` object.  
  
3.  Send the data with `SessionLU0.Send`.  
  
## Example  
 The following code example demonstrates how to send data over an LU0 session using Session Integrator.  
  
```  
private void InsertUserId_Click(object sender, EventArgs e)  
 {  
  try  
   {  
    // Disable every button and text box.  
     DisableEverything();  
     // Enter UserName (SNA200 is what is in the script).  
     // AID = 7D - Enter.  
     byte AID = 0x7D;  
     // Cursor address.  
     byte ca1 = 0x5B;  
     byte ca2 = 0x6B;  
     // SBA  
     byte SBA = 0x11;  
     byte fa1 = 0x5B;  
     byte fa2 = 0xE5;  
     byte[] sna200 = HostStringConverter.ConvertUnicodeToEbcdic("SNA200");  
     byte sixD = 0x6D;  
     byte [] message = new byte [8 + sna200.Length ];  
     message[0] = AID;  
     message[1] = ca1;  
     message[2] = ca2;  
     message[3] = SBA;  
     message[4] = fa1;  
     message[5] = fa2;  
     Array.Copy(sna200, 0, message, 6, sna200.Length);  
     message[6 + sna200.Length] = sixD;  
     message[7 + sna200.Length] = sixD;  
     // Send the data.  
     SessionLU0Data data = new SessionLU0Data();     data.Data = message;  
     // Trace out the data to send.  
     TraceData(true, message, 0);  
     _session.Send(data);  
     // Allow entering director.  
     EnableEnterDirector();  
     }  
    catch (Exception ex)  
    {  
     MessageBox.Show(ex.Message);  
    }  
   }  
```  
  
 Most of this code example is about formatting the data so that the LU can correctly interpret the information; the call to `SessionLU0.Send` is relatively simple. For more information about the code sample, see [Session Integrator for LU0 Code Example](../core/session-integrator-for-lu0-code-example1.md).  
  
## See Also  
 <xref:Microsoft.HostIntegration.SNA.Session>   
 [Receiving Messages with Transaction Integrator for LU0](../core/receiving-messages-with-transaction-integrator-for-lu02.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu01.md)   
 [Session Integrator for LU0 Code Example](../core/session-integrator-for-lu0-code-example1.md)   
 [IcomLU0 Interface](../core/icomlu0-interface1.md)