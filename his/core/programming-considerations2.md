---
title: "Programming Considerations2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 595a64ad-f786-4b9c-92bd-56db67413ac6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Programming Considerations
This topic summarizes information about developing transaction programs (TPs) using APPC on Windows operating systems:  
  
 **Byte ordering**  
 The values of constants defined in WINAPPC.H and WINCSV.H are dependent on the byte ordering of the hardware used. Macros are used to set the constants to the correct value.  
  
 By default, Intel little-endian byte ordering is used, with the low byte of a 16-bit value followed by the high byte. However, when defining inline macros, the NON_INTEL_BYTE_ORDER macro used in WINAPPC.H and WINCSV.H will not reverse (flip) the byte order for constants. Non-constant input parameters in verb control blocks (VCBs) (such as lengths, pointers, and so on) are always in the native format.  
  
 For example, the primary return code of AP_PARAMETER_CHECK is defined to have a value of 0x0001. Depending on the environment (byte ordering), the constant AP_PARAMETER_CHECK may or may not be 0x0001. Some formats define the value as it appears in memory; others define it as a 2-byte variable. Because you cannot assume that the application always uses provided constants rather than hardwired values, you can define a macro to swap the bytes. The following is an example of using the macro:  
  
```  
/* when NON_INTEL_BYTE_ORDER is specified, the APPC_FLIPI macro defined in WINAPPC.H macro becomes */  
#define APPC_FLIPI(x)    (x)  
  
/* otherwise this macro flips bytes by defining */  
#define APPC_FLIPI(X) APPC_MAKUS(APPC_HI_UC(X),APPC_LO_UC(X))  
  
/* the AP_PARAMETER_CHECK macro is now defined using the APPC_FLIPI macro */  
#define AP_PARAMETER_CHECK APPC_FLIPI (0X0001)      /* X '0001' */  
```  
  
 **Events**  
 To receive data asynchronously, an event handle is passed in the semaphore field of the VCB. This event must be in the nonsignaled state when passed to APPC, and the handle must have EVENT_MODIFY_STATE access to the event.  
  
 **Library names**  
 In order to support the coexistence of Win16 and Win32 API libraries on the same computer, the Win32 DLL names have been changed.  
  
|Old DLL names|New DLL names|  
|-------------------|-------------------|  
|WINAPPC.DLL|WAPPC32.DLL|  
|WINCSV.DLL|WINCSV32.DLL|  
  
 The new DLL names should be used for Win32-based applications that are intended to run only on Host Integration Server.  
  
 **Limits**  
 For Windows operating systems, the number of simultaneous common service verbs (CSVs) allowed per process is 64. Only one of these verbs per thread can be synchronous (blocking).  
  
 Using APPC, the maximum number of simultaneous conversations per process is 15,000. Each process supports up to 15,000 simultaneous TPs.  
  
 **Multiple threads**  
 A TP can have multiple threads that issue verbs. Windows APPC makes provisions for multithreaded Windows-based processes. A process contains one or more threads of execution. All references to threads refer to actual threads in the multithreaded Windows environments.  
  
 With the exception of [RECEIVE_AND_POST](./receive-and-post1.md), [MC_RECEIVE_AND_POST](./mc-receive-and-post2.md), [RECEIVE_AND_WAIT](./receive-and-wait2.md), and [MC_RECEIVE_AND_WAIT](./mc-receive-and-wait2.md), only one conversation verb can be outstanding at a time on any conversation; however, other verbs can be issued for other conversations. This guideline also applies to TP verbs and TPs. Although multiple TP verbs can be issued, only one TP verb can be outstanding at a time on a TP. This applies to both multithreaded applications and single-threaded applications that use asynchronous calls.  
  
 **Packing**  
 For performance considerations, the VCBs are not packed. VCB structure member elements after the first element are aligned on either the size of the member type or DWORD (4-byte) boundaries, whichever is smaller. As a result, DWORDs are aligned on DWORD boundaries, WORDs are aligned on WORD boundaries, and BYTEs are aligned on BYTE boundaries. This means, for example, that there is a 2-byte gap between the primary and secondary return codes. Therefore, the elements in a VCB should only be accessed using the structures provided.  
  
 This option for structure and union member alignment is the default behavior for Microsoft C/C++ compilers. For compatibility with the supplied logical unit application (LUA) libraries, make sure to use an equivalent structure and union member packing option when using other C/C++ compilers or when explicitly specifying a structure alignment option when using Microsoft compilers.  
  
 **Registering and deregistering applications**  
 All Windows APPC applications must call [WinAPPCStartup](./winappcstartup1.md) at the beginning of the session to register the application and [WinAPPCCleanup](./winappccleanup1.md) at the end of the session to deregister the application.  
  
 All Windows CSV applications must call the Windows SNA extension [WinCSVStartup](./wincsvstartup1.md) at the beginning of the session to register the application and [WinCSVCleanup](./wincsvcleanup1.md) to deregister the application when the session is finished.  
  
 **Run-time linking**  
 For a TP to be dynamically linked to APPC at run time, the TP must issue the following calls:  
  
- **LoadLibrary** to load the dynamic-link libraries WINAPPC.DLL or WAPPC32.DLL.  
  
- **GetProcAddress** to specify APPC on all the desired entry points to the DLL such as **APPC**, **WinAsyncAPPC**, **WinAPPCStartup**, and **WinAPPCCleanup**.  
  
  For a TP to be dynamically linked to CSV at run time, the TP must issue the following calls:  
  
- **LoadLibrary** to load WINCSV.DLL or WINCSV32.DLL, the dynamic-link libraries for Windows CSV.  
  
- **GetProcAddress** to specify CSV on all the desired entry points to the DLL such as **ACSSVC**, **WinAsyncCSV**, **WinCSVStartup**, and **WinCSVCleanup**.  
  
  The TP must issue the **FreeLibrary** call when the APPC or CSV library is no longer required.  
  
  **Yielding to other components**  
  Because the Windows environments are multithreaded, there is no need to yield to other components.