---
description: "Learn more about: Compiler Options for 3270 Applications"
title: "Compiler Options for 3270 Applications1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6e14f7f-f1e9-4963-81c3-bfe56b6dd102
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Compiler Options for 3270 Applications
When compiling the 3270 client application, the compiler options listed in the following table are required.  
  
|Option|Explanation|  
|------------|-----------------|  
|**/c**|Compile only, without linking. Linking is normally done as a separate phase to include the required Microsoft® Host Integration Server libraries.|  
|**/D NOTRC**|The NOTRC macro specifies that internal tracing should not be compiled into the application.<br /><br /> The **/D NOTRC** option should be used for building a final system (internal tracing should not be included because it will degrade performance and require more memory and resources). For a development system, you may want to compile with internal tracing; if so, remove the **/D NOTRC** option.|  
|**/D WIN32_SUPPORT**<br />**/D MSWIN_SUPPORT,**<br />**/D OS2_SUPPORT,**<br />**/D DOS_SUPPORT**|These macros are used in the header files FMI.H and TRACE.H supplied with SNA services to support variants of the client interface for the different operating systems supported. One of these options must be defined, depending on the operating system for which the application is intended.|  
  
|Option|&nbsp;|Description|  
|-|-|-|  
|**/Gzs**|c:|Use **stdcall** calling conventions on i386/i486 and Pentium class processors.|  
||S:|Remove stack check calls.|  
  
 The compiler flags listed in the following table are required, but any of the valid options for each flag may be used, as appropriate to your application.  
  
|Flag|Description|  
|----------|-----------------|  
|**/A**|Compiler model (Does not apply to Microsoft Windows)|  
|**/O**|Optimization|  
|**/W**|Warning level|
