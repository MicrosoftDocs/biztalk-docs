---
title: "Single Sign-On: Event 10718 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de075c59-8396-48d1-be55-79303f83f984
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10718
## Details  

|                 |                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                     Enterprise Single Sign-On                                                                     |
| Product Version |                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                     |
|    Event ID     |                                                                               10718                                                                               |
|  Event Source   |                                                                              ENTSSO                                                                               |
|    Component    |                                                                                N\A                                                                                |
|  Symbolic Name  |                                                                SSO_ERROR_REPLAY_INCORRECT_ADAPTER                                                                 |
|  Message Text   | Corruption was detected in the replay or progress file.%r<br /><br /> File Name: %1%r<br /><br /> Clear Adapter Name: %2%r<br /><br /> Decrypted Adapter Name: %3 |

## Explanation  
 This Error event indicates that corruption was detected in the replay or progress file.  

 A replay file is stored for a particular password sync adapter so it can be played back as that particular adapter. The adapter name is stored in both clear and encrypted forms. This message indicates that when the replay file was decrypted for playback the decrypted adapter name did not match the adapter name. This can suggest that there has been some corruption or possible tampering with the replay file.  

## User Action  
 To resolve this error, do one or more of the following:  

- Determine why the contents of the replay file might have been modified, see if a backup exists.  

- Check if the SSO master secret was changed or the SSO service account was changed, this could affect encryption behavior.  

- Delete the replay file.  

  For more information, see the following resources:  

- [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  

- [Password Synchronization](../core/password-synchronization2.md)
