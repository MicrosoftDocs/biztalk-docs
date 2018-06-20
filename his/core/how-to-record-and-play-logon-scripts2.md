---
title: "How to Record and Play Logon Scripts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 120d8fcf-b6fd-4e5f-989d-07634bc5424a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Record and Play Logon Scripts
The 3270 logon scripts make it easy for users and administrators to automate the logon procedure. You can use a script provided by your system administrator, or create your own. You can run the logon script at any time. The logon script feature enables Single Sign-On to host applications for the 3270 Host Integration Server clients and 3270 weblets, provided your host security administrator has enabled account password synchronization.  
  
### To use a logon script provided by your system administrator  
  
1.  Start the 3270 Client.  
  
2.  On the **Session** menu, click **Connect**. The **logon** dialog box appears, ready for you to enter your user ID and password.  
  
3.  On the **Script** menu, click **Play**. The script runs, and you are logged on.  
  
### To create your own logon script  
  
1. Start the 3270 Client.  
  
2. On the **Session** menu, click **Connect**. The **logon** dialog box appears, ready for you to enter your user ID and password.  
  
3. On the **Script** menu, click **Record**.  
  
4. Logon to the host using the 3270 screens and keyboard. The **Record** facility converts these actions into a logon script. (Click here to see a [Sample Logon Script](../core/sample-logon-script2.md).)  
  
   When you are finished recording your logon script, on the **Script** menu, click **Stop**.  
  
5. To run your logon script, on the **Script** menu, click **Play**.  
  
   The scripts can be modified using any text editor, such as Notepad.  
  
### To run the logon script automatically each time you connect  
  
1.  On the **Script** menu, select **Auto Run**. When you establish a connection to the host, the logon script runs automatically.  
  
2.  Optionally, on the **Session** menu, select **Autoconnect**. Every time you start the 3270 Client, the connection to the host will be made and you will be logged on automatically.  
  
### To choose different script files  
  
1.  On the **Session** menu, select Session Configuration. The **3270 Settings** dialog box appears.  
  
2.  On the **Script File** box, click **Browse** and select another script file.  
  
3.  Double-click the script file you want to use.  
  
4.  Click **OK**.  
  
## See Also  
 [Sample Logon Script](../core/sample-logon-script2.md)   
 [3270 Client](../core/3270-client2.md)