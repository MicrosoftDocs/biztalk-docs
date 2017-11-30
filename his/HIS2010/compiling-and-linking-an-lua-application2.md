---
title: "Compiling and Linking an LUA Application2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 246f7d51-0e10-46c0-a872-561381e15d91
caps.latest.revision: 3
---
# Compiling and Linking an LUA Application
Use the following procedure to compile and link a logical unit application (LUA) application.  
  
### To compile and link an LUA application for use with Host Integration Server  
  
1.  Update the path statement to include the directory containing the LUA application.  
  
2.  Set any required environmental variables.  
  
3.  Compile the application, including the WINLUA.H header file provided in the Host Integration Server SDK, to produce the .obj files.  
  
4.  Link the application with the WINLUA.LIB library to produce an .exe file.