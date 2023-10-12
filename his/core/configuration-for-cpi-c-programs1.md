---
description: "Learn more about: Configuration for CPI-C Programs"
title: "Configuration for CPI-C Programs1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuration for CPI-C Programs
In addition to maintaining the side information (specified by *sym_dest_name*), the system administrator must define the following entities during configuration:  
  
-   Modes  
  
-   Local logical units (LUs)  
  
-   Partner LUs  
  
-   Invokable programs  
  
-   User identifiers and passwords  
  
> [!NOTE]
>  For a user or group using transaction programs (TPs), 5250 emulators, or Advanced Program-to-Program Communications (APPC) applications, you can assign a default local APPC LU and a default remote APPC LU. These default LUs are accessed when the user or group member starts an APPC program (TP, 5250 emulator, or APPC application) and the program does not specify LU aliases by leaving the field NULL or filling with blanks.
