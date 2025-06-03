---
description: "Learn more about: Compiling and Linking an LUA Application"
title: "Compiling and Linking an LUA Application1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Compiling and Linking an LUA Application
Use the following procedure to compile and link a logical unit application (LUA) application.  
  
### To compile and link an LUA application for use with Host Integration Server  
  
1.  Update the path statement to include the directory containing the LUA application.  
  
2.  Set any required environmental variables.  
  
3.  Compile the application, including the WINLUA.H header file provided in the Host Integration Server SDK, to produce the .obj files.  
  
4.  Link the application with the WINLUA.LIB library to produce an .exe file.
