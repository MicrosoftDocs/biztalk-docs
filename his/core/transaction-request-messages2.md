---
title: "Transaction Request Messages2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 101966a3-7f58-406a-ae72-3fcfd1513b94
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Transaction Request Messages
When you use TCP/IP to communicate with CICS, the client sends the host a transaction request message (TRM) request containing the Transaction Program ID, User ID, Password, and other administrative data to be used by the host. CICS sends the client a TRM reply containing additional administrative data. The data in the TRM is independent from the actual program data to be exchanged with the Transaction Program (TP) on the host.  
  
 You can find templates for various TRMs at \installation directory\Microsoft Host Integration Server\system\TIM\MicrosoftTRMDefs.tim. Use Microsoft Visual Studio to open the file, and then expand the **User-Defined Types** node. The following TRMs are defined as UDTs:  
  
- TRMIN_MSLink  
  
- TRMOUT_MSLink  
  
- TRMIN_MSCCS  
  
- TRMIN_IBMCCS  
  
- TRMOUT_CCS  
  
  You can also find templates for various enhanced listener messages (ELMs) at \installation directory\Microsoft Host Integration Server\system\TIM\MicrosoftELMDefs.tim. Use Visual Studio to open the file, and then expand the **User-Defined Types** node. The following ELMs are defined as UDTs:  
  
- ELMIN_MSLink  
  
- ELMOUT_MSLink  
  
- ELMIN_MSCCS  
  
- ELMIN_IBMCCS  
  
- ELMOUT_CCS  
  
  You can create a TRM or ELM template in COBOL to assist with your programming by exporting the TRM or ELM definition.  
  
### To create a TRM template in COBOL  
  
1. Open Visual Studio.  
  
2. On the **File** menu, point to **Open**, and then click **File**.  
  
3. In the **Open File** dialog box, navigate to \<drive>:\Program Files\Microsoft Host Integration Server\System\TIM\\, and then click either **MicrosoftTRMDefs.tim** or **MicrosoftELMDefs.tim**.  
  
4. On the **File** menu, click **Export Host Definition**.  
  
5. In the **Export Host Definition** dialog box, type or select the file name, and then click **Save**.  
  
   You can substitute a custom TRM (or ELM) for the default TRM (or ELM) created by the TI runtime. Use the COMTIContext parameter to pass custom context data.  
  
## See Also  
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext2.md)   
 [How to Pass a Custom TRM](../core/how-to-pass-a-custom-trm2.md)